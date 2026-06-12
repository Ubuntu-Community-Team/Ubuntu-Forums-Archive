---
title: "CDROM problems???"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by chadd on 2007-05-10
I have been problems with slow downs lately in Feisty.  I tailed my syslog and this is just scrolling by:

May 10 10:17:01 chadd-laptop kernel: [  515.488000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
May 10 10:17:01 chadd-laptop kernel: [  515.488000] sr: Current: sense key: Medium Error
May 10 10:17:01 chadd-laptop kernel: [  515.488000]     Additional sense: Unable to recover table-of-contents


It is locking up my VMware virtual machine as well.  Is this a bug?  Is someone working on it if it is?  Many thanks.

-chadd.

---

### Post by chadd on 2007-05-10
Am I the only one having this problem??  Is there a fix???  PLEASE HELP!!

---

### Post by chadd on 2007-05-11
So, I figured out that if I open the CDROM drive, the messages stop scrolling by.  And so far, after closing it again, the messages have not returned..  Must be a flaky drive.

---

### Post by Evan_G on 2007-06-07
I'm having a similar problem, but with my DVD rom drive.  I'm using Ubuntu 6.10 on this machine.  The dvd drive is an Aopen 16x DVD+/-RW DVD Writer.  I have no problem playing cds and stuff, but when I insert a blank DVD, I get the error:

```
Jun  7 10:08:21 snowball kernel: [17181744.304000] sr0: CDROM (ioctl) error, command: <6>Test Unit Ready 00 00 00 00 00 00
Jun  7 10:08:21 snowball kernel: [17181744.304000] sr: Current: sense key: Medium Error
Jun  7 10:08:21 snowball kernel: [17181744.304000]     Additional sense: Unable to recover table-of-contents
```


This error basically keeps generating itself until I eject the DVD.  The DVD drive works fine in Windows XP, and it worked before when I used Ubuntu 5.10.  I really need to back up some files, so any help would be appreciated.

---

