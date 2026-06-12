---
title: "em8300/hollywoodplus package broken?"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by darktrance on 2005-04-12
I've been banging my head on this one for a while now.  

Attempting to install the em8300_0.14.0-2 package. 
Both the pre and post install scripts fail.  I've tried walking through the scripts manually, but quite frankly, it's beyond my skillset.

Error:
Preconfiguring packages ...
em8300 failed to preconfigure, with exit status 2
Selecting previously deselected package em8300.
(Reading database ... 59431 files and directories currently installed.)
Unpacking em8300 (from .../em8300_0.14.0-2_i386.deb) ...
Setting up em8300 (0.14.0-2) ...
dpkg: error processing em8300 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 em8300
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'd really rather not compile from CVS, anyone get it to work?  pointers?

---

