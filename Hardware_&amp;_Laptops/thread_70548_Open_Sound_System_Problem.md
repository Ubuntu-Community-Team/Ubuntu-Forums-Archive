---
title: "Open Sound System Problem"
date: 2005-09-30
forum: Hardware &amp; Laptops
---

### Post by discreteenmity on 2005-09-30
I'm trying to install oss v3.99.3c but this is the error I get.  I have a m-audio revolution 5.1 and I get just static sounds.

after the /.oss-install command:

Checking for any previously installed sound drivers...
*** Sound driver is already running - trying to unload it ***


You appear to have the the kernel level sound driver installed as a loadable
module. Unload it by executing rmmod sound and try installing OSS/Linux again.

If this error repeats again you probably have the sound driver being loaded
automagically by the kerneld daemon. In this case you should log out from the
X Windows session, then press <ctl><alt><F1> and log in on the Linux console
as root and then install OSS again.

Am I allowed to do these changes automatically for you (Y/N) ? y
Trying to disable the conflicting sound driver

How do I disable my sound driver?  Thanks

---

### Post by discreteenmity on 2005-09-30
I also have ubuntu 5.10 installed if that matters.

---

