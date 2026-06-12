---
title: "Mounting a 2nd HD in Ubuntu"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by antilog on 2005-06-23
I couldn't find exactly what I needed UTSF here or in the starter guide so:

I have a second hard drive that I partitioned ext3 as hdc1.  I do not know how to mount it, nor do I understand the concept;  I am new to linux, decided to switch my one machine over recently.

Thanks for the help, this community has helped me much so far,,,,,

---

### Post by jasmuz on 2005-06-24
[QUOTE=antilog]I couldn't find exactly what I needed UTSF here or in the starter guide so:

I have a second hard drive that I partitioned ext3 as hdc1.  I do not know how to mount it, nor do I understand the concept;  I am new to linux, decided to switch my one machine over recently.

Thanks for the help, this community has helped me much so far,,,,,[/QUOTE]
 to mount do this:

sudo mount /dev/hdc1 /whereverfolderyourwant

To make this permanent ...save the information onto /etc/fstab

---

### Post by afonic on 2005-06-24
You can also read this:
[http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs)

Ignore the NTFS thing, the way is the same (mounting and editing fstab), just do not put the settings for ntfs (follow the example from your other ext3 partitions).

---

### Post by antilog on 2005-07-03
Thanks for the help, I got it!

---

