---
title: "using ssh socks facility to browse to access university library"
date: 2008-08-16
forum: General Help
---

### Post by michibeckd on 2008-08-16
Hallo,

this is my first post, so please be patient with me :-)

I'm trying to setup a ssh connection to my university to get access to resources that are only accessible from computers located at the campus.

My attempt looked as follows:

1: In a shell execute:
   $ ssh -D5000 [email]user@campus.machine.com[/email]

2: Tell firefox to connect to the internet via socks5 (localhost:5000)

My problem is, that even in case I want to browse the online journals at university, I HAVE to set the proper proxy configuration file (PAC) to determine the http proxy that must be used to get access to the ejournals.

And this is my question: How can I tell ssh or my browser or the machine I'm connecting to (I've got no root access there) to use that proxy configuration??

I already tried to set the http_proxy varialble in .bashrc to solve that problem without success.

Any ideas??

Cheers,
michibeckd

---

