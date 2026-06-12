---
title: "Preseed Installation"
date: 2008-12-26
forum: Installation &amp; Upgrades
---

### Post by pete.zhut on 2008-12-26
I have been reading the forums, and the docs; but as yet, I have not found the answer I have been looking for.  I am looking for a start-to-finish howto for using preseed to automate an installation.
  
1. Is it possible to do a fully automated installation?  Meaning, can I drop in the cd, add a simple boot time parameter ( like pointing to a preseed.cfg on a www server ), and then walk away?  

2. If #1 is possible, how?

Thanks all.

---

### Post by woody1ks on 2012-08-07
I saw this thread and thought of your question, hope it helps you. back to my search.

[http://blog.dustinkirkland.com/2012/01/ubuntu-quick-installation-preseed-link.html](http://blog.dustinkirkland.com/2012/01/ubuntu-quick-installation-preseed-link.html)

---

### Post by oldfred on 2012-08-07
I do not know if this still works or not:

Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

---

### Post by Cheesehead on 2012-08-08
> **pete.zhut said:**
> 1. Is it possible to do a fully automated installation?
Yes. It's much easier to use a USB or NetBoot than a CD. Using a CD generally requires altering the image, which is possible (I've done it), but a lot of extra work.

No boot parameter is needed at all...the installer already looks for a preseed file automatically.

> **pete.zhut said:**
> 2. how?
See [https://help.ubuntu.com/11.04/installation-guide/i386/appendix-preseed.html](https://help.ubuntu.com/11.04/installation-guide/i386/appendix-preseed.html) for thorough discussion of preseeding alternatives and excellent instructions. The method for 11.10 or 12.04 is the same.

---

