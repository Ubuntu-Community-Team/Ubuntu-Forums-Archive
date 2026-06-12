---
title: "Ubuntu can't identify my hddisk's partition!"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by anwarlorenzo on 2005-08-05
Hi. Ubuntu doesn't seem to recognize my NTFS partition.

It says:

```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

everytime I try to mount that drive. WinXP can detect it without any problems.
I installed the drive using Seagate's DiskWizard found on [UBCD](http://www.ultimatebootcd.com/). I also used that tool to format it to NTFS.

I hope you guys can help me :)

---

### Post by defkewl on 2005-08-05
You need to enable NTFS from the kernel sources. But I've never done this before.

---

### Post by anwarlorenzo on 2005-08-05
I got one drive with NTFS working but this specific drive won't.

---

### Post by proxess on 2005-11-20
i got a similar problem

I've got 2 ntfs partitions
one is my /dev/hdb5, which is where i keep most of my dls,etc
and the other is /dev/hda1 which is where i have windows and a few small stuff

the thing is on the hard disk info on my hdb5 partition it shows that the filesys is ntfs, which is correct, but on the hda1 partition it shows as unknown, and cause of this i cant mount hda1.

anyone got a sollution?

-thankfully, proxess.

---

### Post by aysiu on 2005-11-20
[QUOTE=anwarlorenzo]
```
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

everytime I try to mount that drive.[/quote] Can you post the output of this command? ```
sudo fdisk -l
``` > WinXP can detect it without any problems. Windows can detect an NTFS partition? Why wouldn't it? NTFS is a proprietary filesystem format that only Windows uses.

[quote=defkewl]You need to enable NTFS from the kernel sources. But I've never done this before.[/quote] I've never had to do this in order to mount an NTFS partition. Never. Never with Ubuntu. Never with another Linux distro.

---

