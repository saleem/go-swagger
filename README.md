# Readme

This is my take on the ![Todo List tutorial](https://goswagger.io/tutorial/todo-list.html) at goswagger.com. 

## Steps

1. Create initial swagger.yml file:

```bash
swagger init spec --title "Todo list" --description "Sample todo list app" --version 1.0.0 --scheme http --consumes application/com.thesaleem.examples.todo-list.v1+json --produces application/com.thesaleem.examples.todo.list.v1+json
```

2. Edit it as as instructed in the tutorial, or as you wish.

3. Create a go module:

```bash
go mod init com.thesaleem/examples/todo-list
```

4. Generate swagger server:

```bash
swagger generate server -A todo-list -f ./swagger.yml
```
This should print out a lot of stuff, ending with two missing packages that you need to get. 

5. *OPTIONAL*: Get the missing packages, like this:

```bash
 go get -u -f ./...
```

6. Install the generated server:

```bash
go install ./cmd/todo-list-server/
```

This will generate a runnable `todo-list-server` and put it in your `$GOPATH/bin` folder. Verify it by doing `ls -la $GOPATH/bin/todo-list-server`. You should **not** get a `No such file or directory`

7. Run the server:

```bash
$GOPATH/bin/todo-list-server
```
This should launch the http server and show you something like this:

```bash
Serving todo list at http://127.0.0.1:54439
```

8. Test your server:
 
```bash
curl http://127.0.0.1:54439
```
This should return `"operation TodosGet has not yet been implemented"`. This is understandable, because we haven't written any implementation for our todo-list yet. However, the API documentation is being served.

