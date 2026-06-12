---
title: "Disk Usage Analyzer wrong?"
date: 2009-04-17
forum: Hardware
---

### Post by Tsula on 2009-04-17
I have Ubuntu 8.10, new install. My hard drive is 250 GB. When I look at the Disk Usage Analyzer it's showing 223 GB total filesystem availablity, almost 3 GB used. Sooo... Where is the 25 odd GB..  Confusing me! Halp. xD

---

### Post by Barry Carroll on 2009-04-17
No it is not wrong.  Your hard drive is 250GB and hard-drives are usually sold in terms of GB or TB which is based on 1000s, so 1GB = 1000MB and 1MB = 1000kB and so on.

Ubuntu and other operating systems use GiB and TiB, in other words they count in 1024s, so 1GiB = 1024MiB and so on.  It's a classic example of hardware vendors misleading consumers in my opinion but it's been done for so long that it seems to be a standard now!

Have a look here for a calculator
[http://wintelguy.com/gb2gib.html](http://wintelguy.com/gb2gib.html)

and here for some more info.

[http://en.wikipedia.org/wiki/GiB](http://en.wikipedia.org/wiki/GiB)

250GB works out to 232GiB

---

### Post by Tsula on 2009-04-17
Awesome, thanks :3

---

### Post by eric9477 on 2009-04-17
I have a laptop running Ubuntu 8.04 with a 10GB hdd (at least that's what was advertised when I bought it back in 2001).  According to the converter posted above, 10GB = 9.31 GiB, but the Disk Usage Analyzer swears that I have a 17.7GB hard drive.  Is the analyzer wrong? :confused:

---

### Post by unutbu on 2009-04-17
Do you have Samba running? Disk Usage Analyzer includes space available in remote Samba directories in its total.

---

### Post by eric9477 on 2009-04-18
No, but I have noticed something funny in the preferences of analyzer.  The list of devices to include in the scan has two entries: /dev/sda1 and gvfs-fuse-daemon.  Both have a total capacity of 8.8GB.  The gvfs-fuse-daemon is mounted in the home directory of sda1 so I'm thinking it's just scanning the sda1 twice somehow right?  At any rate I unchecked it and the numbers in analyzer make more sense now.

---

### Post by caue.rego on 2009-05-11
Well, as you can see on my self-explained-screenshot, for me it ***is*** wrong. Just like for this lone guy:

[http://ubuntuforums.org/showthread.php?p=1963145](http://ubuntuforums.org/showthread.php?p=1963145)

I think this issue might be on not scanning hidden stuff, but I just don't know or care. I just deleted it anyway. :P

---

### Post by Wiebelhaus on 2009-06-05
> **caue.rego said:**
> Well, as you can see on my self-explained-screenshot, for me it ***is*** wrong. Just like for this lone guy:

[http://ubuntuforums.org/showthread.php?p=1963145](http://ubuntuforums.org/showthread.php?p=1963145)

I think this issue might be on not scanning hidden stuff, but I just don't know or care. I just deleted it anyway. :P

I'm getting wrong output if I'm reading a mounted HDD but if it's local then it reads correctly.

I have to fix this and when I do , I'll update it here.

---

### Post by caue.rego on 2009-10-16
my DUA always read wrong comparing to DU and actually disk usage. it doesn't matter which partition or mounted disk (although I don't have any external disk to mount other than pen drives).

I just chose that vista partition on my local disk because it wouldn't present any permission errors. you can see on that picture I run DU on it without SU and still get different results for several directories.

that problem persists up to today.

---

