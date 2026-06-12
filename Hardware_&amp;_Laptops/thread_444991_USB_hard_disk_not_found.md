---
title: "USB hard disk not found"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by pohlipit on 2007-05-15
Hi,

I am trying to connect a HDD via USB. It works fine on Windows and usually when I connect any memory stick or other HDD via USB there is no issue. But this one is just not being recognised at all. 

I am running Feisty on a Thinkpad T43. When running on my Windows partition it's no problem but on Feisty no chance. It's a Hitachi HDD in a Transcend USB box.

Can anyone help please.

Thanks,
 Pete

---

### Post by TheWizzard on 2007-05-15
please post the output of
```
sudo sfdisk -l
```

---

### Post by TheWizzard on 2007-05-15
what kind of format is the hdd? for exchange you'd use fat32 rather than ntfs.

---

### Post by pohlipit on 2007-05-15
> **TheWizzard said:**
> please post the output of
```
sudo sfdisk -l
```

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   2731    2732-  21944758+   7  HPFS/NTFS
/dev/sda2       2732   11605    8874   71280405   83  Linux
/dev/sda3      11606   14280    2675   21486937+  83  Linux
/dev/sda4      14281   14592     312    2506140   82  Linux swap / Solaris

Disk /dev/sdb: 9729 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an MSDOS signature
 /dev/sdb: unrecognised partition table type
No partitions found

It's NTFS format. Oh, and since the drive is the original one from the T43 it has 2 partitions. The main one and a "hidden" one at the end where the rescue & recovery software from the Thinkpad is being placed.

P!

---

### Post by TheWizzard on 2007-05-18
am i correct that you did take your HDD from the think pad and put it in a hdd casing with usb connection?
the out put from sfdisk shows that linux doesn't recognise the file system. 

i'm not sure what's the best thing to do. i think reformatting helps, but this erases your data.

---

