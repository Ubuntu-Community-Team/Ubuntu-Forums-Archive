---
title: "swapon failed: Invalid argument"
date: 2011-06-29
forum: Hardware
---

### Post by Freaky#Funga on 2011-06-29
Hi there,
I'm trying to swap to file on my sdcard, but I'm getting this error
```
swapon failed: Invalid argument
```
Here is the sequence to produce the error
```
root@eee:/media/sd1# dd if=/dev/zero of=/media/sd1/hibernate.img bs=1024k count=200
200+0 records in
200+0 records out
209715200 bytes (210 MB) copied, 18.7177 s, 11.2 MB/s
root@eee:/media/sd1# mkswap /media/sd1/hibernate.img 
mkswap: /media/sd1/hibernate.img: warning: don't erase bootbits sectors
        on whole disk. Use -f to force.
Setting up swapspace version 1, size = 204796 KiB
no label, UUID=81c367ac-5301-4af6-8681-40e2297b6d5c
root@eee:/media/sd1# swapon /media/sd1/hibernate.img 
swapon: /media/sd1/hibernate.img: swapon failed: Invalid argument
```

Here is my mount part
```
/dev/sdb1 on /media/sd1 type btrfs (rw,nosuid,nodev,compress)
```

When I create this file on my root filesystem (ext4) it works fine.

Any suggestions?

---

### Post by Sylos on 2011-06-29
Hello there.

Im afraid I cant help with your problem but I do have a question about it. Why are you trying to swap to an SD card. I assume this is connected via usb so would the connection not be too slow to gain any benefit from having swap enabled to it?

Just a thought...

---

### Post by Freaky#Funga on 2011-07-03
> **Sylos said:**
> Hello there.

Im afraid I cant help with your problem but I do have a question about it. Why are you trying to swap to an SD card. I assume this is connected via usb so would the connection not be too slow to gain any benefit from having swap enabled to it?

Just a thought...

I don't actually want to swap to that partition (I have plenty of free memory and primary swap place on SSD drive). I want to hibernate to this file and since I upgraded my RAM, the primary swap place is too small.

---

### Post by Michun on 2011-07-09
I've got the exact same problem with a swapfile on a compressed btrfs.
And I suspect the problem is right there: **the compression**. I will try it with an uncompressed mount (but once coompress was used, btrfs is tainted with it).

Gerhard

---

