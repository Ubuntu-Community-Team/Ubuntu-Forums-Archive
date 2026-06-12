---
title: "Cant boot into Ubuntu"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by acmariner99 on 2009-01-11
Here is my setup and process:

40 GB ext3 partition (Ubuntu)
500Mb swap
40GB fat32 (XP)- just installed

process:

installed Ubuntu and used Ubuntu partitioner to set up hard drive
installed XP to fat32 partition

can no longer boot into Ubuntu, default to XP

what can I do to add Ubuntu to xp's mbr

---

### Post by taurus on 2009-01-11
You just need to reinstall GRUB back to MBR since windows overwrote it when you installed windows.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by acmariner99 on 2009-01-11
Ok, grub is up and running, but how do I find where xp is and add it to grub so it will boot (hd0,0) etc, or could you be more specific as to how to add xp to grub.

---

### Post by taurus on 2009-01-11
If your windows resides on /dev/sda3, then the entry in /boot/grub/menu.lst for it would look something like

```

title Windows XP
rootnoverify (hd0,2) 
makeactive
chainloader +1

```

Remember to add it to the bottom of /boot/grub/menu.lst.

---

### Post by acmariner99 on 2009-01-11
I get error 13: invalid or unsupported executable format when I try to boot into xp

---

### Post by acmariner99 on 2009-01-11
figured it out, I have two functional OS's now! (Windows is only good for gaming, need it for nothing else!) Thx!

---

### Post by taurus on 2009-01-11
What's the output of this command from a terminal (in Ubuntu)?

```
sudo fdisk -l
```

---

