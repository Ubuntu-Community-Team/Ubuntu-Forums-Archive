---
title: "Swap is not enabled, even though I have some"
date: 2008-05-24
forum: Hardware
---

### Post by ezramorris on 2008-05-24
Hi,
I did a bit of repartitioning of my hard disk, and I still have a swap partition, but it was changed. However, in system monitor>resources, there is no swap activated.

I read somewhere about comparing the UUID from sudo blkid with a couple of files, they were set incorrectly. I updated them, but swap is not enabled.

```
ezra@ezra-laptop:~/Downloads$ sudo swapon -a
swapon: cannot canonicalize 8ca27d82-6ae0-4ae0-a260-a795298ae2a5: No such file or directory
swapon: cannot stat 8ca27d82-6ae0-4ae0-a260-a795298ae2a5: No such file or directory

```

The only work around I have found is to enable it in Partition editor, but this is only temporary, and the problem happens again at reboot.

Any ideas?

---

### Post by Sam Lars on 2008-05-24
I've had this happen before to me, too.  Try doing an mkswap on your swap partition and using the UUID it gives you from that.

---

### Post by ezramorris on 2008-05-24
> **Sam Lars said:**
> I've had this happen before to me, too.  Try doing an mkswap on your swap partition and using the UUID it gives you from that.

OK, I'm an idiot.
I did what you suggested, and got the UUID. However, I was just about to copy it in to /etc/fstab, when I noticed that the line just had the UUID, rather than UUID=<UUID>

](*,) So simple...

---

