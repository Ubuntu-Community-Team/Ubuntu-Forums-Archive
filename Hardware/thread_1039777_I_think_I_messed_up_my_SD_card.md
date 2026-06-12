---
title: "I think I messed up my SD card"
date: 2009-01-14
forum: Hardware
---

### Post by bigboyman2 on 2009-01-14
I have a 4 GB micro SD card I use for my G1. Each time I mounted it onto my laptop, it always opened up f-spot and loaded all the pictures up, and displayed several errors. I didn't want it to automatically open f-spot on mount, so I took a look at the mount options

Mount point: /media/disk
file system: vfat
Mount options: rw nosuid nodev relatime uid=1000 fmask=0077 dmask=0077 codepagecp437 iocharset=iso8859-1 shortname=mixed utf8

Now, being the absolute genius I am, I proceed to delete **all** the mount options, except for rw. Now, I unmounted it, then tried to re-mount it, all I get is an error that says

"You are not privileged to mount this volume"

I go into the terminal and type

```
joel@Ninja:~$ sudo mount /media/disk
mount: can't find /media/disk in /etc/fstab or /etc/mtab

```


I'm in a little over my head in this case, I would really like some help!

---

### Post by bigboyman2 on 2009-01-15
Also, to give a little more insight, the SD card works fine in Windows 7 (dual booting), and works fine while in my G1, I just can't mount it while in ubuntu

---

### Post by bigboyman2 on 2009-02-13
Er, I'm not sure what happened. It started working again, and I haven't messed with it since I made the first post. If anyone could tell me how I can stop it from opening up all my pictures in f-spot, then that would be great. Otherwise, it's working now *scratches head*

Edit: Never mind, I just removed f-spot. I never use it, actually. I'll marked this as solved, I guess

---

