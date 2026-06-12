---
title: "Reverting to Older Version of Ubuntu"
date: 2008-08-18
forum: General Help
---

### Post by ShredTheSilence on 2008-08-18
Okay so I downloaded the Ubuntu 8.04 from the site and burned the .iso to a cd to install. I come to find out after installing 8.04 that my broadband card doesn't work so well with it (or not at all.) So i figure i still have the 7.04 install disc why not revert. Instead my computer refuses to recognize the install disc. 

Any Suggestions?

---

### Post by wilbbe01 on 2008-08-18
I would suggest figuring out how to fix the support for the card.  What kind of card do you have?

---

### Post by silkstone on 2008-08-18
It sounds as if your original CD may have degraded, which they can over time.

wilbbe01's suggestion is probably the best, but you should be able to download 7.04 from...

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by ShredTheSilence on 2008-08-18
A Sprint Mobile Broadband Card by Franklin Wireless.

---

### Post by wilbbe01 on 2008-08-18
> A Sprint Mobile Broadband Card by Franklin Wireless.

And that card worked in a previous version of Ubuntu?  If it did, did you have to do anything to get it to work?

---

### Post by ShredTheSilence on 2008-08-19
Yes in 7.04 through the terminal i Typed,

sudo apt-get install connect-proxy

and afterwords you install it and then you connect through

cd Desktop/Linux_Ubuntu

sudo ./connect

I tried to do the same thing in 8.04 and i get this message,

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  connect-proxy
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 18.6kB of archives.
After this operation, 81.9kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe connect-proxy 1.96-1 [18.6kB]
Fetched 18.6kB in 1s (12.7kB/s)    
Selecting previously deselected package connect-proxy.
(Reading database ... 98051 files and directories currently installed.)
Unpacking connect-proxy (from .../connect-proxy_1.96-1_i386.deb) ...
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up connect-proxy (1.96-1) ...
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wilbbe01 on 2008-09-10
Did you end up figuring this out?  I'm not sure as to what the proxy url stuff is doing, but it shouldn't say [http://:8080/:](http://:8080/:)  That could be a problem.

---

