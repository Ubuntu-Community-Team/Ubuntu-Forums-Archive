---
title: "can't mount ext4 after update"
date: 2010-01-11
forum: Hardware
---

### Post by Björn on 2010-01-11
Hi everybody, i was away on christmas holidays and when i came back ubuntu wanted to update kernel and some other stuff, then of course i had to reboot into the new kernel. When it started it got stuck and so i rebooted into recovery mode and it seems like it cannot mount the root partition.

I tried to film it and put it on youtube so you could see but the quality aint the best. Try it in HQ and pause it (EDIT try pause at 0:16) and you can see almost everything.

[http://www.youtube.com/watch?v=IW8A2YuZflI](http://www.youtube.com/watch?v=IW8A2YuZflI)

I get almost the same if i try to mount sda4 manualy. None of the old kernels work either.

An ideas?

Dualboot vista (not used in over a year but it still works) ubuntu on EXT4 sda4.

Thanks for any help

/Björn

---

### Post by Björn on 2010-01-12
Okey, i booted from a bootable cd and ran Gparted and made a check. This was the outcome:
```

GParted 0.4.3

Libparted 1.8.8
Check and repair file system (ext4) on /dev/sda4  00:00:35    ( ERROR )
     	
calibrate /dev/sda4  00:00:00    ( SUCCESS )
     	
path: /dev/sda4
start: 115668000
end: 304479944
size: 188811945 (90.03 GiB)
check file system on /dev/sda4 for errors and (if possible) fix them  00:00:35    ( ERROR )
     	
e2fsck -f -y -v /dev/sda4
     	
/dev/sda4: recovering journal
JBD: Failed to read block at offset 28277
e2fsck 1.41.4 (27-Jan-2009)
/dev/sda4: Attempt to read block from filesystem resulted in short read while reading block 11595381

e2fsck: Input/output error while recovering ext3 journal of /dev/sda4

========================================

```

---

