---
title: "[SOLVED] Can't access HD with xubuntu liveCD"
date: 2008-08-25
forum: General Help
---

### Post by Stoodle on 2008-08-25
My uncle was experiencing problems with his computer so I decided that I'd use my xubuntu CD, back up his hard drive, reinstall XP, and place xubuntu on the side. Well, I couldn't access his hard drive! It doesn't show up with a name and I went through hell trying to find it in all of the directories. Never did find it so I'd like to know what to do.

Also, my hard drive didn't show up when I popped it into my computer  whereas I can see my hard drive with the ubuntu 7.04 CD. Using ubuntu in his computer wasn't an option since he had 256 mb of ram.

---

### Post by rraj.be on 2008-08-25
Try in this location

```
/media
```

---

### Post by Stoodle on 2008-08-26
I did and only my external hard drive shows up.

---

### Post by -Zeus- on 2008-08-26
> **Stoodle said:**
> I did and only my external hard drive shows up.

post the output of ```
sudo fdisk -l
``` and ```
df
```

---

### Post by Stoodle on 2008-08-30
Well, I got it working. I popped in an older Ubuntu CD, I think it was 7.04 or 6.10. I saw the name of the hard drive but it said it couldn't mount. Well, the information I got basically said that because I had done a hard reset in Windows, shutdown was never written to one of the log files. Therefore, Linux thought that I had Windows running from that hard drive and wouldn't let me mount the hard drive. I did some command... I think it was
```
sudo mount -t ntfs-3g /dev/sda2 /media/PRESARIO -o force
```
That's off that top of my head so it's probaby not quite that. However, I was able to force a mount and copy my uncle's hard drive. Only the older Ubuntu discs show the name of the hard drive even if it's not mounted. It's there for you to mount. Also, in order to have found the hard drive, I had to first go to places and then filesystem. It didn't show up when on the desktop until I did that. Anyway, I figured it out.

---

