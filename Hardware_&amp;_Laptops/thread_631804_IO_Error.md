---
title: "I/O Error"
date: 2007-12-04
forum: Hardware &amp; Laptops
---

### Post by goldencako on 2007-12-04
I have this brand new 2G, Kingston SD disk for my digital camera which started giving me errors. At first it had problems reading and writing, but now it doesn't do any of the two. I'm not too worried about that anymore, since I needed it urgently and had to buy another one. However, I do have some data I would do anything to recover on the Kingston disk. I used this command to try to get the data:

```
sudo cp -fv /media/disk/DCIM/101SSCAM/* /Pictures
```

and for every file the output is something analogous to this:

```
`/media/disk/DCIM/101SSCAM/SS850754.JPG' -> `/Pictures/SS850754.JPG'
cp: reading `/media/disk/DCIM/101SSCAM/SS850754.JPG': Input/output error
```

By now I'm pretty much sure I'll just have to say goodbye to those pictures, but hey, hope dies last. So if anyone has any ideas on how to recover the data I would immensely appreciate it. A program, an obscure command, or anything really. By the way, I had the disk reformatted a few times when it started failing. And I'm running a dual boot Gutsy Gibbon/XP Media Center, and on the XP I had the same error, but I was able to preview a few images, despite not being able to copy them.

Thanks in advance for any help.

---

### Post by Friek on 2007-12-06
If you're lucky, it just needs a filesystem repair. I guess it's formatted with vfat (as most cams use that filesystem), so you can try fsck.vfat on it.

---

### Post by goldencako on 2007-12-06
> **Friek said:**
> If you're lucky, it just needs a filesystem repair. I guess it's formatted with vfat (as most cams use that filesystem), so you can try fsck.vfat on it.

I ran df to find out what was the name of the device and i got:

```
/dev/mmcblk0p1         1996416    600128   1396288  31% /media/disk
```

So I tried using fsck.vfar but it just gave me some information about the device:
 
```

$ fsck.vfat /dev/mmcblk0p1 
dosfsck 2.11, 12 Mar 2005, FAT32, LFN

```

I got the same reults for options -a and -r. So I ran dosfsck::
```

$ dosfsck  /dev/mmcblk0p1 
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/mmcblk0p1: 191 files, 18754/62388 clusters

```

And again I get the same results using options -a or -r.
I'm probably wrong on the syntax to repair, so please tell me how to do it.

---

### Post by Friek on 2007-12-09
Did you umount it before doing the fsck?

---

### Post by goldencako on 2007-12-17
No. Did I have to?

---

