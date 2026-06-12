---
title: "Format floppies: need help"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by ceti on 2005-04-23
Please help me to format '1.44 diskettes. I tried with both GFloppy Formater and KFloppy but got these error messages:

GFloppy: Error formatting track #0
KFloppy: Cannot access /dev/fd0u 1440. Make sure that the device exists and that you have write permission to it.

Thanx

ceti

---

### Post by Burgundavia on 2005-04-23
There are a couple of reasons that this could be. 
1. Your floppy drive is toast
2. Your floppy drive is not seen by Ubuntu
3. Your floppies are toast

I suspect number 2 and 3, but 1 is possible.

Corey

---

### Post by David Haas on 2005-04-23
I format floppies with shell commands as follows: "fdformat /dev/fd0". Then I add the Linux filesystem with: mke2fs /dev/fd0". Please let me know how this goes and if you have further questions.
David Haas

---

### Post by ceti on 2005-04-24
[QUOTE=David Haas]I format floppies with shell commands as follows: "fdformat /dev/fd0". Then I add the Linux filesystem with: mke2fs /dev/fd0". Please let me know how this goes and if you have further questions.
David Haas[/QUOTE]

:-P Thank you, David.
It worked perfectly.
Cheers
ceti

---

### Post by ensenadaubuntulover on 2005-05-26
[QUOTE=David Haas]I format floppies with shell commands as follows: "fdformat /dev/fd0". Then I add the Linux filesystem with: mke2fs /dev/fd0". Please let me know how this goes and if you have further questions.
David Haas[/QUOTE]


tried to do that but I get this response...

Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ...
ioctl(FDFMTTRK): Device or resource busy

any ideas?

---

### Post by David Haas on 2005-05-26
I'm not familiar with the message you received while attempting to format your floppy: "ioctl(FDFMTTRK): Device or resource busy". while waiting for someone else to help you with this, you could look at fstab in /etc. Mine looks like this for the floppy : /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0. I chose /media/floppy0 as my mount directory, but this doesn't matter for your problem. In the 4th column, "noauto" would seem to be what you want to prevent a boot-time mount of the floppy. Because the message stated "Device or resource busy" I wonder whether automount could be the problem . 
David

---

### Post by ensenadaubuntulover on 2005-05-26
[QUOTE=David Haas]I'm not familiar with the message you received while attempting to format your floppy: "ioctl(FDFMTTRK): Device or resource busy". while waiting for someone else to help you with this, you could look at fstab in /etc. Mine looks like this for the floppy : /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0. I chose /media/floppy0 as my mount directory, but this doesn't matter for your problem. In the 4th column, "noauto" would seem to be what you want to prevent a boot-time mount of the floppy. Because the message stated "Device or resource busy" I wonder whether automount could be the problem . 
David[/QUOTE]



I dont know much, but what I did was :

sudo umount /dev/fd0 

an then it worked perfect, so far I dont do that anymore and can still format the floppies every time I boot the machine it is a mistery for me but worked

thanks for your time anyway I apreciate!

---

