---
title: "after upgrade to 9.10,  cannot start x"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by webrp on 2009-11-10
Hi,

I have just made an upgrade on my ubuntu from 9.04 to 9.10, and after reboot I am stuck in the command line. I make login but cant get out from the command line shell. I attempted the  startx command but no success, "server failure".

-during upgrade I was asked what to make to grub configuration file, wich I have choosen to leave intact (dont know if this matters)

What can I do to get my ubuntu desktop back?

---

### Post by RedSingularity on 2009-11-11
Try making a new xorg file with this command........

sudo dpkg-reconfigure xserver-xorg

---

### Post by kio_http on 2009-11-11
DO you have an NVIDIA graphic card?

If so you need to reinstall driver from NVIDIA site as your kernel has changed.

---

### Post by webrp on 2009-11-11
I am now back on Ubuntu, and problem is solved.

I am not sure how I have managed this. I guess what I did right was editing /etc/X11/xorg.conf and editing there some line to "Driver sis671". After a big struggle with VI editor I cant remember what I have done exactly.
I have also attempted to "reset" this file with command "sudo dpkg-reconfigure -phigh xserver-xorg" but no changes are made in file.

Could somebody tell me what wents wrong? I am trying to learn a little bit.

---

