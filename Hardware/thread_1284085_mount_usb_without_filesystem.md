---
title: "mount usb without filesystem"
date: 2009-10-06
forum: Hardware
---

### Post by AwesomeTux on 2009-10-06
So, I have this USB thumb drive, and I think it got its filesystem destroyed, either by electric shock for magnet (if that's possible) and I want to try and mount it before throwing it away, like, it doesn't auto-mount, and probably doesn't have a filesystem.

How would I either mount it, locate it, or create a filesystem on it?

I believe it's recognized, but just can't mount, but how would I see if it's recognized as well?

Thanks :P

---

### Post by AwesomeTux on 2009-10-06
Yep, found it with lsusb so it recognizes it...

```
jacob@jacob-ubuntu:~/Desktop$ lsusb 
Bus 001 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by ajgreeny on 2009-10-06
Try gparted to format to a filesystem of your choice, though you will have to unmount it first, or you will not be able to do anything to it.

---

### Post by AwesomeTux on 2009-10-06
> **ajgreeny said:**
> Try gparted to format to a filesystem of your choice, though you will have to unmount it first, or you will not be able to do anything to it.

I've tried that. It doesn't show the unallocated space/partitions. And it doesn't even say that it found it, yet the command 'lsusb' does.

---

### Post by renkinjutsu on 2009-10-06
see if it has a device name linked to a "block image"

sudo blkid (i hope it works)

then use that device name with mkfs

---

### Post by AwesomeTux on 2009-10-07
> **renkinjutsu said:**
> see if it has a device name linked to a "block image"

sudo blkid (i hope it works)

then use that device name with mkfs

That worked great! :guitar: That is exactly what I was looking for! Thank you man!

Now I don't have to throw it away :P

---

### Post by renkinjutsu on 2009-10-07
xD no problem man

My internet was down the whole day, and when it was back up, this thread was the first thing i checked.. I get a good feeling when i'm able to help ;)

---

