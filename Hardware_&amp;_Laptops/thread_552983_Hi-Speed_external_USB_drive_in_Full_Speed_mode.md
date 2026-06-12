---
title: "Hi-Speed external USB drive in Full Speed mode"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by pdwhittaker on 2007-09-17
I've got an external USB hard drive (Western Digital MyBook, 320Gb, separate power supply) plugged into my Feisty desktop machine.  The machine and the drive both support Hi-Speed USB:

```
$ sudo hdparm -t /dev/sdb2

/dev/sdb2:
 Timing buffered disk reads:   88 MB in  3.04 seconds =  28.92 MB/sec

```

In the past (under Dapper / Edgy) I occasionally noticed a problem where the drive would fall back to Full Speed mode (without me doing anything other than reading/writing files to it).  Speeds were then around 1Mbyte/second; this made some tasks painfully slow.  This was normally when it was taking some heavy use, but since that was the only time that I'd actually notice it happening, it might not have been the cause.  

As I'm using that drive more now, I sometimes notice that it's only mounted at Full Speed after booting: right-clicking the drive icon -> Properties -> Drive tells me "Connection: USB 2.0 at 12 Mbps".  After I unmount the drive and do ```
sudo modprobe -r ehci-hcd ; sudo modprobe ehci-hcd
``` I see "USB 2.0 at 480Mbps" instead, and I can get the hdparm output listed above.  This is then quite stable as far as I can tell.  I've also been able to get Hi-Speed back in the past by pulling the power connector out of the drive(!) then putting it back in again - it gets re-detected at Hi-Speed, and again appears stable.

Can anybody suggest what might be causing my drive to be connected at the slower speed?  I'd quite like to not have to do the modprobe trick every time I need to use the drive at Hi-Speed.  If anyone could suggest useful tests I might do to try and narrow things down, I'll be happy to give them a try.

---

### Post by pdwhittaker on 2007-09-22
Problem is still there.  Also, the drive reconnects at a different location after redetection is forced - could this indicate that it's being handled by a different part of the driver?  Here's what I've just seen (the interesting partition of the drive is mounted as /media/myBook):

```
$ # drive already automatically mounted when I log in
$ mount | grep Book
/dev/sdf2 on /media/myBook type ext3 (rw,nosuid,nodev)
$ sudo hdparm -t /dev/sdf2
/dev/sdf2:
 Timing buffered disk reads:    4 MB in  4.02 seconds = 1017.85 kB/sec
$ # drive at sdb, and slow.

$ sudo umount /media/myBook
$ sudo modprobe -r ehci-hcd ; sudo modprobe ehci-hcd
$ # drive remounts automatically

$ mount | grep Book
/dev/sdb2 on /media/myBook type ext3 (rw,nosuid,nodev)
$ sudo hdparm -t /dev/sdb2
/dev/sdb2:
 Timing buffered disk reads:   88 MB in  3.06 seconds =  28.77 MB/sec
$ # drive at sdf, and fast.

$ # Why doesn't it start off this way?
```

Any suggestions as to how I can get this mounted with the right driver in the first place will be much appreciated! :)

---

### Post by pdwhittaker on 2007-10-28
If anyone else is getting this problem, it appears to be the same issue as:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/66115")

I haven't tried updating /etc/initramfs-tools/modules and running update-initramfs; I'm using umount / modprobe / mount to fix the problem when it turns up, as mentioned above.

---

