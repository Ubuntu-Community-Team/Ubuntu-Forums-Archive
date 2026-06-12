---
title: "Ubuntu Server installation"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by alexius on 2009-06-22
I need to install a server for a 20 user network. The requirement is to manage email uploads and downloads, manage windows updates (all the users use Windows), and virus updates as well as to do backups for users.
Any suggestions of the best way to achieve this. I have lots of experience with MS servers - but have never installed a Linux server before. Which server distro would you recommend?
How difficult will it be to achieve the results desired as above?
I am an IT professional of many years - but not an Ubuntu expert! :confused:

---

### Post by Mighty_Joe on 2009-06-22
> **alexius said:**
> . . . manage windows updates (all the users use Windows), and virus updates. . .

I'm not a Linux power user, but I don't think Ubuntu Server is going to have many tools to help you with Windows-specific tasks like the above.  And if by "email" you actually mean "Outlook/Exchange Server", I don't think it can be done with Ubuntu (or Linux in general) .
That said, Ubuntu Server is probably a good choice for many tasks, like those in this [list of features]("http://www.ubuntu.com/products/whatisubuntu/serveredition/features")

---

### Post by alexius on 2009-06-22
Thanks Mighty-Joe - I checked out some alternatives and Ebox, which is based on Ubuntu, seems to offer some great features - [http://www.ebox-technologies.com/](http://www.ebox-technologies.com/)
Anyone have any comments on Ebox?

---

### Post by scrooge_74 on 2009-06-22
I'm lost here, sorry for my question, what exactly you want to achieve? Manage windows updates and antivirus updates? <--- aint this done by the windows programs when they do their updates?

Or you want to set up a mail server for internal use?

---

### Post by alexius on 2009-06-22
The client is trying to cutdown on expensive bandwidth usage (in South Africa). 20 users each updating 100Mbs in a month will cost the client 2Gb of bandwidth. He wants one download - and all users do updates from a cache/repository type of system. I am still looking into this.
Secondly - he just wants a mail server to again prevent hectic bandwidth internally. Users are sending each other emails (internally) with large files and pictures and he does not want the emails to be sent to external POP server and then straight back to the network.

By the way - also looking at SME Server - which seems very good - any comments?

---

### Post by scrooge_74 on 2009-06-23
If all PC were linux based I have seeing instructions on making the server work like a repository, but for windows I have no clue.

You still can make a mail server and a proxy to cut their bandwith use

---

