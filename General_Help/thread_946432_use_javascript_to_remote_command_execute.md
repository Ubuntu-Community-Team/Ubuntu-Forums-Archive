---
title: "use javascript to remote command execute"
date: 2008-10-13
forum: General Help
---

### Post by belaviyo on 2008-10-13
Hi there

I want to be able to access to remote shell from JavaScript, then send some command and receive answer

As I know it is impossible to use ssh with JS, so I can use Putty for this purpose. Can any body help how can do this

---

### Post by jespdj on 2008-10-13
Can you explain in more detail what you want to do? Do you have something like this in mind:
[LIST=1]
[*]The user uses a webbrowser to go to a webpage with some JavaScript.
[*]The JavaScript code executes some shell command on the user's computer.
[*]The JavaScript reads the output of the shell command and sends it back to the web server.
[/LIST]
If that's what you want to do, then that's not possible, and for good reasons! It would be a huge security hole if it would be possible to run arbitrary programs on a client computer like this.

---

### Post by belaviyo on 2008-10-13
Not really 

What I want is to execute a command on remote machine by asking for user name and password from JavaScript

some apps like Putty can make a ssh connection and run commands on remote machine and then retrieve answer

I want to do this with JavaScript

---

