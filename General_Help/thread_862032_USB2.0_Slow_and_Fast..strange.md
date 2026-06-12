---
title: "USB2.0 Slow and Fast..strange"
date: 2008-07-17
forum: General Help
---

### Post by fouadz on 2008-07-17
Transfer speed

I'm having an issue with Ubuntu. Here is my setup
- 1 physical hd devided in two partitions (1 of it's FAT32 )
- USB 2.0 HardDrive

The transfert is very very slow from my Ext3 partition to my USB 2.0 HD. I'm getting 2.0mb/s average rate.
But from my FAT32 partition to my USB 2.0 I doing 20mb/s .

I just dont get it.


```


Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda6     ext3     38G   21G   15G  59% /
varrun       tmpfs    501M  236K  501M   1% /var/run
varlock      tmpfs    501M     0  501M   0% /var/lock
udev         tmpfs    501M   52K  501M   1% /dev
devshm       tmpfs    1.0G   12K  1.0G   1% /dev/shm
lrm          tmpfs    501M   39M  463M   8% /lib/modules/2.6.24-19-generic/volatile
tmpfs        tmpfs    1.0G   12K  1.0G   1% /dev/shm
/dev/sdb1     ext2    296G   22G  260G   8% /media/disk
/dev/sda3     vfat     17G  9.1G  7.9G  54% /media/disk-1



root@kungfu:/var/log# hdparm -tT /dev/sda6 /dev/sda3

/dev/sda6:
```

```
root@kungfu:/var/log# hdparm -tT /dev/sda6 /dev/sda3 /dev/sdb1

/dev/sda6:
 Timing cached reads:   2154 MB in  2.00 seconds = 1077.73 MB/sec
 Timing buffered disk reads:  132 MB in  3.01 seconds =  43.82 MB/sec

/dev/sda3:
 Timing cached reads:   2164 MB in  2.00 seconds = 1082.97 MB/sec
 Timing buffered disk reads:  102 MB in  3.06 seconds =  33.37 MB/sec

/dev/sdb1:
 Timing cached reads:   2082 MB in  2.00 seconds = 1041.57 MB/sec
 Timing buffered disk reads:   92 MB in  3.04 seconds =  30.24 MB/sec
```


Any idea !?

---

### Post by danwood76 on 2008-07-17
What format is your USB disk?

I would be its fat, there is a conversion of file names and stripping permissions when going from ext3 -> fat.
On most systems this extra overhead is negligable, I get ~20MB/s from my ext3 partitions to my fat USB disk.
It could just be that this extra overhead is causing your system to transfer the files slowly.

What spec is your machine?

---

### Post by fouadz on 2008-08-01
my both partitions are ext3 and I also formated the usb hd to be ext3.
I have a dual core with 1gig of ram.

As I said before from my second parition to the usb hd it's smokkiing fast.
But from my primary to the HD it's soo sllooowwww.

Too weird for me...I dont get it.

---

