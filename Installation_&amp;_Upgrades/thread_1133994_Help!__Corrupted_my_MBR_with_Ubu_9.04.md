---
title: "Help!  Corrupted my MBR with Ubu 9.04?"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by CK009 on 2009-04-23
Hi,

I have a Vista x64 partition and just installed Ubuntu 9.04 to a separate partition.  I didn't resize anything, but did click yes to overwriting the MBR.  

The problem is that Vista has disappeared from the boot menu when I restart the computer.  I've tried inserting the Vista disk to repair this, but it doesn't detect Vista in the first place.  Please help! 

Thanks in advance..

---

### Post by CK009 on 2009-04-23
Figured it out.  Will post again later to explain incase anyone has the same problem.

---

### Post by Trevster on 2009-04-23
Post the output of:

sudo fdisk -l

It will list all the partitions on you machine.

---

### Post by CK009 on 2009-04-23
[INDENT]$ sudo fdisk -l
Unable to seek on /dev/sda
[/INDENT]Maybe that's related to my RAID 0 setup?  Also seems to prevent mounting of the windows partition.

Otherwise the MBR problem was resolved by: -

1.  sudo gedit /boot/grub/menu.lst

2.  Inserting the following before the 3 Ubuntu options and after "## ## End Default Options ##": -
[INDENT] title Vista 64-bit
root        (hd0,2)
savedefault
makeactive
chainloader    +1
[/INDENT]Overall, Ubuntu is really impressive.  Last time I used Linux was ~10 years ago (Slackware) and things have come a really long way.  Unfortunately, the software I rely on for work (e.g. Invitrogen Vector NTI 11, Graphpad Prism 5, Adobe InDesign / Illustrator CS4) are not WINE compatible.  Sweet OS though =)

---

