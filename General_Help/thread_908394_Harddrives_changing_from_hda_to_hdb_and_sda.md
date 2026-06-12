---
title: "Harddrives changing from hda to hdb and sda"
date: 2008-09-02
forum: General Help
---

### Post by Solidcell on 2008-09-02
So I'm trying to set up a harddrive of mine to mount on bootup (it's NTFS, but that's irrelevant).  I've added it to /etc/fstab, and sometimes it'll mount on boot.  Sometimes it doesn't because it will boot with a different label (or whatever you call 'hda1' or 'sda1').  If it happens to boot with hda1 (or whatever I put in /etc/fstab last), then it works, but sometimes it'll boot as sda1 or hdb1.

I don't get it, I haven't opened the case (let alone changed jumpers or moved the HDDs around).  Why is the harddrive not consistently hda1?  In the last 10 minutes I've rebooted 4 times and I've noticed the HDD being hda1, hdb1, and sda1.  Why does it bounce around?  I need to be able to add it to /etc/fstab, this is driving me crazy!

---

### Post by bingoUV on 2008-09-02
Well, it happens. Your hard disks are extra bouncy but kernel updates frequently cause this anyway so relying on device name (hda, sda etc) to be constant is never a good idea. 

In fstab, add uuid entry instead of device name i.e. the first field in fstab file is the device identifier. Suppose it is /dev/sdf2. Do
```

ls -l /dev/disk/by-uuid/

```

See the UUID file pointing to /dev/sdf2. That is the UUID, of the form 97311b9-5a10-42b0-b2c1-a9404cea55b2. In your fstab, replace entry for /dev/sdf2 by 
```

UUID=97311b9-5a10-42b0-b2c1-a9404cea55b2   /mount/point ....other options ...

```

---

### Post by Solidcell on 2008-09-02
Awesome!  Thanks so much bingo, that worked perfectly.  You the man.

---

### Post by xinematik on 2008-10-02
Same problem here. 
Solved :D :D 

Good help bingoUV !
Thanks

---

