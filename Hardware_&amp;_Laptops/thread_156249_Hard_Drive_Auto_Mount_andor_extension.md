---
title: "Hard Drive Auto Mount and/or extension?"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by green1152 on 2006-04-06
Here's my problem:
I'm using an older computer which had Windows 98 on it. I reformatted everything, got Ubuntu on on the first master drive after some trouble. It was a little weird, the hard drive was routed through a card on the motherboard, and not through an IDE.

Anyway, I got that working, and the drive is called SDA1 on here.

Now what I want to do is to add another 120 gig hard drive as either a seperate hard drive all together to store media on, or to make it an extension of this little 4 gig master drive.

I believe the drive is all connected right. It shows up in Ubuntu and in knoppix as HDD1 for some reason. I am able to browse and write to it in admin mode from ubuntu, but I am having trouble from there. I'm new to Ubuntu and Linux, so I am need of some help.

Thanks.

---

### Post by ubuntuuser on 2006-04-06
So, what exactly is your problem? If you want it to be mounted automatically, add the following line to your /etc/fstab:
```
/dev/hdd1       /media/hdd1               ext3    defaults       0      0
```
If your drive is fat32, use this instead:
```
/dev/hdd1       /media/hdd1  vfat    umask=000        0       0
```
If your problem is another, please be more specific.

---

