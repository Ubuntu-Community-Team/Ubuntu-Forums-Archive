---
title: "Password Protection using Webmin"
date: 2008-08-02
forum: General Help
---

### Post by batMouse on 2008-08-02
Hi Everyone, 
 
Before we go anywhere I'll put my hands up and warn you that I am fairly new to the Linux Operating system in general - so everything is going quite slowly for me at the moment! I have however, come across an extremely frustrating problem of which I have found one post in the forum from before, but have yet to find an answer to. I would therefore be extremely appreciative for any input which might lead to the solution!! 
 
Basically, I've used Webmin to set up a web server on my desktop. Apache 2.2 (I think that's the right version!) is installed and I have changed my DocumentRoot to the directory that I would like to post to the internet. This is working as intended, and I am able to view my files no problem - I have also set up Port Forwarding to bypass my router. 
 
However, I then want to password protect this DocumentRoot directory - so that I am able to use it as a private file storage area. I have tried to do this using webmin's password protect directory feature - which works fine, creates the required .htaccess and .htpasswd files - but does NOT make any difference to my site whatsoever, with no request for a password.  
 
I've also tried manually creating the .htaccess and .htpasswd files myself through terminal, but something that I found strange was that these files, after creation, do not show up in terminal when using the ls command - yet they still exist to edit using gedit. It seems like they are hidden... weird?! 
 
Thanks a lot for any advice you can give, not going anywhere with it at the moment!

---

### Post by batMouse on 2008-08-02
Anybody? :/ Still unable to sdolve this problem. Thanks!

---

### Post by ChumleyEX on 2008-08-02
make sure your using

> ls -a

if any files starts with a . it makes it hidden while doing a normal ls. 

 I hope this helps.

---

