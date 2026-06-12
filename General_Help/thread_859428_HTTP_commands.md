---
title: "HTTP commands"
date: 2008-07-14
forum: General Help
---

### Post by cleopard on 2008-07-14
I'm wondering about HTTP and the commands used to fetch a page.  From what I've read, if I want to do it from the command line using 'telnet', I enter 'telnet' <URL> <port number>, like I do in my example below.  Then, I type the GET command followed by the page and 'http/1.1'.  Yet when I do this, nothing is ever fetched and the connection is closed; here's an example:


craig@craig-smith-0:~/fetch/cyntrs/emhttpc$ telnet [www.google.com](www.google.com) 80
Trying 64.233.167.99...
Connected to [www.l.google.com](www.l.google.com).
Escape character is '^]'.
GET [http://www.google.com/advanced_search?hl=en](http://www.google.com/advanced_search?hl=en) http/1.1
Connection closed by foreign host.


But if I take off the 'http/1.1', data is returned:

craig@craig-smith-0::~/fetch/cyntrs/emhttpc$ telnet [www.google.com](www.google.com) 80
Trying 64.233.167.99...
Connected to [www.l.google.com](www.l.google.com).
Escape character is '^]'.
GET [http://www.google.com/advanced_search?hl=en](http://www.google.com/advanced_search?hl=en)         
<html><head><meta HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1"><title>Google Advanced Search</title><style>div,td,.n a,.n a:visited{color:#000}.ts td,.tc{padding:0}.ts,.tb{border-collapse:collapse}.ti{display:inline}.ti{display:inline-table}.f{color:#666}.flc,a.fl{color:#7
.
.
.
etc, etc, proceeds to fetch the page.

Also, after entering the GET command line, I was then supposed to type in a line something like:   **Host: [www.google.com:80](www.google.com:80)**
but after entering the GET command and hitting return, I don't get time to enter the 'Host:' command, and it goes ahead and fetches the data without it.  What's going on?  Any help would be appreciated.

---

### Post by hal8000 on 2008-07-14
A Telnet session is used to establish communication with a remote communications device e.g.  teleprinter, satellite receiver or can be used to check mail on a mail server.

You are telnetting to a google web page, so not sure what youre trying to acheive??

Are you thinking of ftp?  With ftp, you can connect to a remote site, broswe its contents and uplaod or download files using get and put commands.

---

### Post by cleopard on 2008-07-14
Go to:

[http://en.wikipedia.org/wiki/Http#Request_methods](http://en.wikipedia.org/wiki/Http#Request_methods)

and enlarge the sample screenshot on the right and you'll get a better idea of what I'm referring to.

---

### Post by fragos on 2008-07-14
Why not use "wget http://www.google.com/advanced_search?hl=en" and avoid all the telenet confusion. The file will be placed in the working directory.

---

### Post by ral0r3us on 2008-07-18
> **cleopard said:**
> I'm wondering about HTTP and the commands used to fetch a page.  From what I've read, if I want to do it from the command line using 'telnet', I enter 'telnet' <URL> <port number>, like I do in my example below.  Then, I type the GET command followed by the page and 'http/1.1'.  Yet when I do this, nothing is ever fetched and the connection is closed; here's an example:


craig@craig-smith-0:~/fetch/cyntrs/emhttpc$ telnet [www.google.com](www.google.com) 80
Trying 64.233.167.99...
Connected to [www.l.google.com](www.l.google.com).
Escape character is '^]'.
GET [http://www.google.com/advanced_search?hl=en](http://www.google.com/advanced_search?hl=en) http/1.1
Connection closed by foreign host.


But if I take off the 'http/1.1', data is returned:

craig@craig-smith-0::~/fetch/cyntrs/emhttpc$ telnet [www.google.com](www.google.com) 80
Trying 64.233.167.99...
Connected to [www.l.google.com](www.l.google.com).
Escape character is '^]'.
GET [http://www.google.com/advanced_search?hl=en](http://www.google.com/advanced_search?hl=en)         
<html><head><meta HTTP-EQUIV="content-type" CONTENT="text/html; charset=ISO-8859-1"><title>Google Advanced Search</title><style>div,td,.n a,.n a:visited{color:#000}.ts td,.tc{padding:0}.ts,.tb{border-collapse:collapse}.ti{display:inline}.ti{display:inline-table}.f{color:#666}.flc,a.fl{color:#7
.
.
.
etc, etc, proceeds to fetch the page.

Also, after entering the GET command line, I was then supposed to type in a line something like:   **Host: [www.google.com:80](www.google.com:80)**
but after entering the GET command and hitting return, I don't get time to enter the 'Host:' command, and it goes ahead and fetches the data without it.  What's going on?  Any help would be appreciated.

Man HTTP1.1 did work you just didnt realize, you saw a blinking promt 
right? This happened for the simple reason that HTTP 1.1 supports 
persistent connections, which means you were actually connected but you 
needed to issue a new command. Try this:

```
telnet www.somewebserver.com 80
GET / HTTP/1.1
GET /
etc..
```
you will see that the server responds. If you want you can also pipe 
through this connection a script that has all these commands, that way you
 make sure your connection with the web server doesn't timeout.

Actually this is what web browsers do (not exactly but close), they take
 your request parse it, insert the commands, open a socket and pipe the 
whole text (commands + request) in. The reason why simply with GET worked,
 is because you didn't specify which version to use so the host assumed 
(most hosts do that, if not all) you are using an older version of HTTP, 
the idea behind that is back compatibility with older versions of 
browsers.

 So since versions of HTTP prior to 1.1 didn't support persistent 
connections, you get your request served and the connection is closed.  
 

P.S. You don't have to issue again the [http://www.somehost](http://www.somehost).....
 part again after you have established a connection to the server. If you 
do this it's like typing in a browser 
[http://www.somehost.comhttp://www.somehost.com/](http://www.somehost.comhttp://www.somehost.com/)

---

