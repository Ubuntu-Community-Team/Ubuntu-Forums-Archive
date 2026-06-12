---
title: "Another question about installing ubuntu on external Hard Drive..."
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by jef1013 on 2009-05-16
I know, there are a lot of these questions out there, but I have a question.  When installing Ubuntu 9.04 to my external Hard drive, do I need to install Grub on the internal HD or can I simply install grub only on the external HD.  I am having problems.  I installed Ubuntu on my external HD and it went well but when I try to boot up, the initramfs comes up and gives me an error saying that: root=uuid= (a bunch of numbers) cannot be found.  I've tried setting the root = /dev/sdb5 (the last partition on the external HD) but to no avail.  

What I simply want to do is the following:

1) Install Ubuntu 9.04 x86_64 on my external HD
2) Leave everything untouched on my internal HD
3) Be a Happy Ubuntu User...

Thanks in advance !

---

### Post by marshall.robert on 2009-05-16
If you are installing on to an external drive I would recommend that you disconnect your internal ones first. It helps with avoiding confusion with the bootloader, I have seen many times that grub installs its self on to the internal drives which causes an error when booting without the external drive plugged in.

---

### Post by exchequer598 on 2009-05-16
Yeah well I did disconnect my internal HDD!!

---

