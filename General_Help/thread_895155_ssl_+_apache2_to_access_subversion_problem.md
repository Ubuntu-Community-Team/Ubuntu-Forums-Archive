---
title: "ssl + apache2 to access subversion problem"
date: 2008-08-19
forum: General Help
---

### Post by mickey13 on 2008-08-19
Hi all,

I have a subversion repository running that I can access using Apache2.  So my checkout looks like:

[http://[IP](http://[IP) Address]/svn/[Repository name]

I haven't had a lot of luck getting this to work with the SSL added on top.  I've looked through some forums already, but haven't tried anything that has worked for me.  I've created a certificate using make-ssl-cert.  I've set up a virtual host (and enabled it) for "ssl".  Here's the error I get when I try to check out using:

http**s**://[IP Address]/svn/[Repository name]

Error: PROPFIND request failed on '/svn/[Repository name]'  
Error: PROPFIND of '/svn/[Repository name]': could not connect to server ([https://[IP](https://[IP) Address])  

Anyone know what I could try from the given errors?  Let me know if more info is needed.  Thanks in advance for the help!

---

### Post by mickey13 on 2008-08-20
How does Apache2 know to use the ssl virtual host that I setup when https is used instead of http?

How do I check that Apache2 is doing that?

Also, should the document root be the same as the default virtual host?

Thanks.

---

### Post by mickey13 on 2008-08-27
When I create the security certificate, I put "localhost" for the hostname.  Anyone know if that's correct or not?

---

### Post by tlacuache on 2008-08-27
This tutorial was helpful for me when I set up subversion:

[http://alephzarro.com/blog/2007/01/07/installation-of-subversion-on-ubuntu-with-apache-ssl-and-basicauth/](http://alephzarro.com/blog/2007/01/07/installation-of-subversion-on-ubuntu-with-apache-ssl-and-basicauth/)

---

### Post by mickey13 on 2008-08-27
Thanks for the link!  On step 4: Create Virtual Host, what did you put for $SITENAME?  Is that the name of the repository, or something else?  Thanks again.

---

