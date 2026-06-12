---
title: "2nd Harddrive Problem"
date: 2009-02-05
forum: Hardware
---

### Post by jamrop on 2009-02-05
Hey

I installed a new hard drive and set up to work with /media/stream, all working, but it failed once, so i changed it to just /nas and got it to share, which worked great, but now it has gone back to stream, and i am not sure why

I had a look at my /etc/fstab, and it had the /nas2 setup, but it still working in media/stream, its a bit confusing hehe, as i do a lot of file transfers, and have to keep swapping about

Any idea how to keep it as /nas2

Many thanks

---

### Post by jamrop on 2009-02-05
Had a look at gparted, it seems to have changed from /dev/sda1 to /dev/sbd1

Can not seem to mount sbd1 tho

---

### Post by taurus on 2009-02-05
Open a terminal and post the outputs of these commands here.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```
Instead of using /dev/sda1 or /dev/sdb1 (not /dev/sbd1), you should consider using UUID for that drive in /etc/fstab.

---

### Post by jamrop on 2009-02-06
hey

thanks for reply, will fdisk -1 format the drive tho? as i have data on it

Not sure what you mean when you say UUCID, never heard of it

many thanks

---

