# Part 0 - Fundamentals of Web apps

Course overview: It provides an initial understanding of the course, covering fundamental concepts such as HTTP requests, the functioning of traditional web applications, DOM, CSS, and Single Page Applications.

[new note](./0.4.mmd) - Diagram illustrating browser-server communication: The diagram illustrates the interaction between the browser and the server when a user adds a note to a page with JavaScript. 
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser ->> server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of browser: The browser transmits a text/html file to the server, which includes the content "Hello."
    server -->> browser: HTTP Status 302 - Found
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server -->> browser: HTTP Status 200 - OK Return text/html
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server -->> browser: HTTP Status 200 - OK Return text/css
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server and refresh the page
    server -->> browser: HTTP Status 200 - OK Return aplication/js
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server -->> browser: HTTP Status 200 - OK Return aplication/json
    deactivate server
    Note right of browser: The browser executes the callback function that renders the notes
```

[SPA](./0.5.mmd) - Single-page app communication: The diagram depicts how the browser and server communicate when a user opens a single-page app in the browser.

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server -->> browser: HTTP Status 200 - Ok Return text/html
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server -->> browser: HTTP Status 200 - OK Return text/css
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    server -->> browser: HTTP Status 200 - OK Return application/javascript
    deactivate server

    browser ->> server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server -->> browser: HTTP Status 200 - OK Return aplication/json
    deactivate server
    Note right of browser: The browser executes the callback function that renders the notes
```

[SPA new note](./0.6.mmd) - Adding a note to a single-page app: The diagram showcases the communication between the browser and the server when a user adds a note to a single-page app.
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser ->> server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of browser: The browser transmits a text/html file to the server
    Note left of server:  server push the content in note Array {content: "Hello", date: "2024-01-31T22:23:10.544Z"}

    server -->> browser: HTTP Status 201 - Created
    deactivate server
    Note right of browser: The browser executes the event handler that renders the notes
```