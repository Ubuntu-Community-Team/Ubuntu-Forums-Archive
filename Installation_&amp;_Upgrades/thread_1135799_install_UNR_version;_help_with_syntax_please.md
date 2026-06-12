---
title: "install UNR version; help with syntax please"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by pdc on 2009-04-24
I hope I am posting in the correct forum;

I wanted to look at the Ubuntu Netbook Remix; I have successfully downloaded it, and verified with the checksum;

I run OpenSuse on a desktop; I wanted to look at UNR for our Eee;

so I cannot use ImageWriter I understand;

I have the downloaded ubuntu-9.04-netbook-remix-i386.img on a USB stick

> /dev/sdd1

and I want to convert it to a bootable USB device, that will be 

> /dev/sdc1

so, trying to follow the advice from 

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

I have firstly run the command

> sudo umount /dev/sdc1 (*intended target USB stick*)

then 

> sudo dd if=/dev/sdd1/ubuntu-9.04-netbook-remix-i386.img of=/dev/sdc1/ bs=1M

and getting the error message

> dd: opening `/dev/sdd1/ubuntu-9.04-netbook-remix-i386.img': Not a directory

grateful for advice

---

### Post by pdc on 2009-04-24
I reverted to using the Download directory on the hard drive as source;
and again sent the .img to sdc1 and my syntax was obviously better, as it has transferred to the USB stick; and it has now booted on the Eee;


a bientot, mes amis

---

