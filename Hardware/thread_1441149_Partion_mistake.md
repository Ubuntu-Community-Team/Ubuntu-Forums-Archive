---
title: "Partion mistake"
date: 2010-03-28
forum: Hardware
---

### Post by terbor on 2010-03-28
I was formatting a few external drives yesterday and realized after it was to late that I removed the first partition from my maxtor external hard drive by mistake.  I am using cfdisk or I can use fdisk if it helps fix the issue. 

Anyway I have like 100GB of info that I want to access.  Is there anyway to set the partitions back?  The file format was ntfs and I tried just mounting it again, but no luck.  Thanks.

```
robert@hatTrick:~$ lsscsi
[0:0:0:0]    disk    ATA      SAMSUNG HD080HJ  ZH10  /dev/sda
[1:0:0:0]    cd/dvd  PBDS     CDRWDVD DH-48C2S ND11  /dev/sr0
[9:0:0:0]    disk    Maxtor   OneTouch III     0344  /dev/sdb

root@hatTrick:/media# mount -t ntfs /dev/sdb /media/maxtor/
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@hatTrick:/media# ls /dev/sdb*
/dev/sdb
```

---

### Post by srs5694 on 2010-03-28
Try using the testdisk program to scan your disk for the missing partition.

---

### Post by varunendra on 2010-03-28
First of all, make sure whatever tool you use doesn't write on the disk!!

Second, have you heard about "Hiren's Boot CD"? It contains some very powerful tools that may solve your problem. It's about 186Mb iso image. Download, burn & boot from it....

Good Luck!

---

### Post by varunendra on 2010-03-28
> **srs5694 said:**
> Try using the testdisk program to scan your disk for the missing partition.

Yes, testdisk is also a very small commandline tool but very powerful for dealing with new, lost or corrupt partitions. cheers!

---

### Post by efflandt on 2010-03-28
sdb is a drive, not a partition.  You certainly cannot mount a "drive" as ntfs.  The first partition would be /dev/sdb1.

Removing a partition does not destroy any data on it, but to get it back you have to recreated it in the same exact place and size.

You say you removed the "first" partition by mistake.  Does that mean that the partition(s) that followed it are still in place.  If so then it may be easy to use fdisk to create it again from the beginning to as far as it can.

But if you also removed the following partition, it gets more complicated.

I tried to see if I could change a primary partition into a logical partition within an extended partition once, and that did not work.  So I changed back into a primary partition and everything was still there.

It was a bit more complicated when 64-bit WinXP beta totally changed the drive geometry of my partition table so it could not even boot itself.  Unfortunately I had not saved the output of fdisk after shrinking my XP home partition before that.  But fortunately I remembered the heads, calculated the cylinders, and had to experiment with partition end points in fdisk until everything worked (no data lost).

---

### Post by terbor on 2010-03-29
efflandt - there was only one partition. So it was sdb1 that I removed.  Thanks for pointing me to testdisk.  That was very easy to follow.  I got my partition back and it works again.

---

### Post by varunendra on 2010-03-29
Congrats! So now you should mark the thread as "Solved".

---

