⚡ sparkplug
========

`sparkplug`, like its predecessor [`gin`](https://github.com/codegangsta/gin), is a simple command line utility for restarting your Go server in a development setting. `sparkplug` improves upon gin by using [filesystem notifications](https://github.com/fsnotify/fsnotify). Furthermore, `sparkplug` exposes an HTTP endpoint to facilitate manual restarts if need be.

Like `gin`, `sparkplug` adheres to the "silence is golden" principle, so it will only complain 
if there was a compiler error or if you succesfully compile after an error.

## Installation

Assuming you have a working Go environment and `GOPATH/bin` is in your 
`PATH`, `gin` is a breeze to install:

```shell
go get github.com/skeswa/sparkplug
```

Then verify that `sparkplug` was installed correctly:

```shell
sparkplug -h
```

## Usage

In your terminal, navigate to the source directory of your web server, then execute:
```shell
sparkplug
```
Once compiled, your server will then be exposed on port 3000 or the specified by the `PORT` environment variable.  
The server may be restarted by changing any source file, or by requesting the [/restart](http://localhost:3000) HTTP endpoint (this endpoint is configurable).

## Supporting Sparkplug in Your Web app
`sparkplug` assumes that your web app binds itself to the `PORT` environment 
variable so it can properly proxy requests to your app. Web frameworks 
like [Martini](https://github.com/go-martini/martini) do this out of 
the box.

## Using flags?
When you normally start your server with [flags](https://godoc.org/flag)
if you want to override any of them when running `sparkplug` we suggest you 
instead use [github.com/namsral/flag](https://github.com/namsral/flag)
as explained in [this post](http://stackoverflow.com/questions/24873883/organizing-environment-variables-golang/28160665#28160665)
