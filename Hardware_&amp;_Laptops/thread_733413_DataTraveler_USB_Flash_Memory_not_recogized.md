---
title: "DataTraveler USB Flash Memory not recogized"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Jack Vrouwes on 2008-03-23
I use Ubuntu Gutsy.

I have two USB flash memory keys:
(1) a Verbatim Store'n'Go 1Gb, and
(2) a Kingston DataTraveler DT1 1Gb.

(1) Automounts normally under all conditions.
(2, the DataTraveler) presents the following automounting problems.

(2) will be normally recognized and display when I insert it and subsequently boot.  However, it will not be recognized anymore after I safely eject it and reinsert it thereafter.

Now, if according to the Kingston FAQ, I do "sudo mkdir /mnt/flash", and add
"/dev/sda1  /mnt/flash vfat user,noauto,umask=0 0 0" to /etc/fstab I can repeatedly use 
"mount /mnt/flash", and unmount it on right-clicking.   So far so good.

However, if I interrupt this sequence with using (1), (2) will not mount anymore afterwards.  The error message is then:
"mount: special device /dev/sda1 does not exist."

This result is consistent and reproducible. How can I interchangebly use both memory keys?  Is there something wrong with HAL, and how do I work around it?

---

