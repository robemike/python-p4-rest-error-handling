# Error Handling In RESTful APIs

## Learning Goals

- Build RESTful APIs that are easy for other developers to understand and use
  in their own applications.

***

## Key Vocab

- **Representational State Transfer (REST)**: a convention for developing
  applications that use HTTP in a consistent, human-readable, machine-readable
  way.
- **Application Programming Interface (API)**: a software application that
  allows two or more software applications to communicate with one another.
  Can be standalone or incorporated into a larger product.
- **HTTP Request Method**: assets of HTTP requests that tell the server which
  actions the client is attempting to perform on the located resource.
- **`GET`**: the most common HTTP request method. Signifies that the client is
  attempting to view the located resource.
- **`POST`**: the second most common HTTP request method. Signifies that the
  client is attempting to submit a form to create a new resource.
- **`PATCH`**: an HTTP request method that signifies that the client is attempting
  to update a resource with new information.
- **`PUT`**: an HTTP request method that signifies that the client is attempting
  to update a resource with new information contained in a complete record.
- **`DELETE`**: an HTTP request method that signifies that the client is
  attempting to delete a resource.

***

## Introduction

Try as we might, it is impossible to build a robust API without the possibility
of errors and exceptions. Common issues include:

1. Creating records that already exist.
2. Creating, retrieving, updating, or deleting resources while your database
   server is down.
3. Creating or updating records with invalid attributes.
4. Retrieving, updating, or deleting records that don't exist.

The guiding principle of the REST philosophy is that the behavior of an API
should be predictable. So how do we handle these cases outside of the
functionality of our API in a predictable way?

***

## HTTP Error Codes

Just like request methods, HTTP also specifies a number of response status codes
to help the client understand if and why their request was successful. We've
already talked about some status codes in earlier modules:

1. 200 (OK) means that the request was successful. This can be used for any
   request method, though it is not always the most descriptive. That being
   said, the client will be less interested in descriptive codes when requests
   are successful.
2. 201 (Created) means that the request was successful in creating a new
   resource. This is the best code to use after a successful `POST` request.
3. 404 (Not Found) means that the request was unsuccessful because it attempted
   to access a resource that does not exist on the server. After 200, this is
   the most common status code in a well-built API.

Codes are grouped by the hundreds:

- **100s** are informational. They inform the client that some process is being
  carried out before a final response is sent.
- **200s** denote a successful request.
- **300s** let the client know that a redirect is taking place. This is usually
  because a resource has been moved- _you should avoid doing this in RESTful
  APIS_.
- **400s** are client errors. They let the client know that _they_ made a
  mistake.
- **500s** are server errors. They let the client know that something is
  temporarily out of order on your server.

Let's explore the error codes a bit further:

### 400-Class Codes: Client Errors

400-class status codes are intended as responses to client errors. These codes
can be sent in response to any request method.

Despite their error, it is still our duty as developers (especially RESTful API
developers) to give the client an informative message describing what went
wrong.

The most common 400-class response codes are:

- **400 (Bad Request):** the server is unable or not permitted to process the
  request, usually due to metadata in messages or forms.
- **401 (Unauthorized) and 403 (Forbidden):** the user has not logged in _or_
  has logged in but is not permitted to access the resource.
- **404 (Not Found):** as mentioned above, this means that the resource being
  sought after by the client does not exist.

For more information on 400-class codes, check out the [Mozilla documentation][
400].

### 500-Class Codes: Server Errors

500-class status codes are acknowledgements that the server has produced an
error. It is _critically important_ to let the client know that a 500-class
error has occurred and whether it is due to regular maintenance, a bug, or a
permanent change.

**500 (Internal Server Error)** is by far the most common 500-class error. It
can be appropriately used for nearly every server-side error, and with an
appropriate and informative message, it is more than sufficient to meet the
client's needs.

That being said, there are several other 500-class status codes for specific
cases. For more information on 500-class codes, check out the
[Mozilla documentation][500].

***

## Exception Handling in Flask

.

### Custom Error Messages

.

***

## Conclusion

.

***

## Resources

- [Handling Application Errors - Pallets](https://flask.palletsprojects.com/en/2.2.x/errorhandling/)
- [Client error responses - Mozilla][400]
- [Server error responses - Mozilla][500]
- [8. Errors and Exceptions - Python](https://docs.python.org/3.8/tutorial/errors.html)

[400]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses
[500]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server_error_responses
