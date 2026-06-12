---
title: "Suspend and Hibernate: resume instantly!"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by samba on 2005-05-11
Hi,

I just installed Hoary on my Dell Inspiron 8100. Everything works fine, even suspend to RAM and hibernate seem to work fine! However, there is a slight problem: it suspends, or hibernates, but resumes instantly... not very useful!

To make it work I followed the wiki [http://ubuntulinux.org/wiki/HoaryPM](http://ubuntulinux.org/wiki/HoaryPM). I have a NVIDIA video card, but i use the open source driver, so it seems to work fine.

Anyone knows what I can do to stop it from resuming instantly after going to sleep?

Thanks for your help! :-)

and thanks for the good work, ubuntu is wonderful! :-)

---

### Post by samba on 2005-05-11
The problem was the following.

Although i am not using the NVIDIA drivers (i'm using the open source ones), i tried to install them previously (but it didn't work so i remodified my /etc/X11/xorg.conf file to use the nv driver again). However, I forgot to remove the nvidia modules from my /etc/modules file, so, although not used, this module was loaded. And it seems that this nvidia module was the problem, since now i did "modprobe -r nvidia" and suspends and hibernates works fine! :-)

cheers
Samba

---

