---
title: "Hard Drive Only Writable As Root"
date: 2017-02-05
forum: Hardware
---

### Post by mike32442 on 2017-02-05
I have a hard drive mounted into a folder in my home directory that is only writable as root.
The following is from fstab


LABEL=Movies3 /home/mike/morefilms auto nosuid,nodev,nofail,x-gvfs-show 0 0

The permissions are set as follows

drwxrwxrwx 4 mike mike      4096 Feb  5 10:28 morefilms

Any assistance in solving this would be greatly appreciated.

Thanks

---

### Post by TheFu on 2017-02-05
Which type of file system?
What is under /home/mike/morefilms?

BTW, 777 is only good for testing. Please don't use those permissions ... er .... ever.

---

### Post by mike32442 on 2017-02-08
It is an ext4 filesystem, the folder contains media files, and I know 777 is a bad idea and was my last go at getting access at user level.

Thanks

---

### Post by TheFu on 2017-02-08
> **mike32442 said:**
> It is an ext4 filesystem, the folder contains media files, and I know 777 is a bad idea and was my last go at getting access at user level.

What is the output from **mount | grep  /home/mike/morefilms** ?

Here's one of my ext4 mounts, as an example.  I don't use gvfs; find it slow.
```
$ mount |grep /D
/dev/mapper/istar-vg-lv_media on /D type ext4 (rw,errors=remount-ro)

```

---

