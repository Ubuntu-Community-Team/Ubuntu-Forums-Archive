---
title: "Oracle 11g install problems"
date: 2008-04-06
forum: Georgia Team - US
---

### Post by larryduncan on 2008-04-06
I am getting two messages while trying to install Oracle 11g and i am sure it is preventing me from installing Oracle, I am running Ubuntu 7.10 and I get the following errors while trying to install.

 unknown user oracle

 Couldn't find package lib

Please help.

---

### Post by siafulinux on 2008-04-06
> **larryduncan said:**
> I am getting two messages while trying to install Oracle 11g and i am sure it is preventing me from installing Oracle, I am running Ubuntu 7.10 and I get the following errors while trying to install.

 unknown user oracle

 Couldn't find package lib

Please help.

You might be able to just add a user with "sudo adduser oracle". As for missing "lib" was it "lib-something" or just lib? 

JC

---

### Post by larryduncan on 2008-04-07
It was originally libaio1 but I found a script to install that package.  Is this seperate or related.

Thanks for your help.

---

### Post by siafulinux on 2008-04-07
> **larryduncan said:**
> It was originally libaio1 but I found a script to install that package.  Is this seperate or related.

Thanks for your help.

Looks like it's related in the sense that it concerns databases; hope that helps. Visit 
[URL="http://packages.ubuntu.com/feisty/libs/libaio1"]http://packages.ubuntu.com/feisty/libs/libaio1
[/URL] for more, but to quote from the page:

>  libaio1 - This library enables userspace to use kernel asynchronous I/O system calls, important for the performance of databases and other advanced applications. 

---

