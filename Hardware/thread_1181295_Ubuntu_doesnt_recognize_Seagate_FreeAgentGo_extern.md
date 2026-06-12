---
title: "Ubuntu doesnt recognize Seagate FreeAgent|Go external HD"
date: 2009-06-07
forum: Hardware
---

### Post by JonDobbs on 2009-06-07
Why doesnt Ubuntu recognize Seagate FreeAgent|Go external HDs? I get an error message about how the drive is unmountable.

Also, does anyone happen to know how to open the casing on the new FreeAgent|Go?

---

### Post by Jekshadow on 2009-06-07
I had some problems with my SeaGate, and it turned out to be a simple formatting thing (It was NTFS), I just installed [COLOR="DarkRed"][Gnome Partition Manager]("apt:gparted")[/COLOR] and deleted the partition, then made a FAT32 partition. Note: click the link above to install Gnome Partition Manager, open the page "apt:gparted" in firefox or konquer (without quotes), or type this in any terminal:

```
sudo apt-get install gparted
```

---

### Post by sgosnell on 2009-06-07
What version of Ubuntu are you using?  Google shows that when the Freeagent drives came out in December 2007 they didn't work under Linux, but later kernels fixed the problem.  The current kernels read NTFS drives just fine, and are supposed to recognize and use the Seagate drives.  I've avoided Seagate for several years, so I can't say if they really do work.

---

