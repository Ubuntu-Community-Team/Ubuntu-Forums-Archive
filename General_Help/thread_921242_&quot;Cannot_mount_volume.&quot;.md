---
title: "&quot;Cannot mount volume.&quot;"
date: 2008-09-16
forum: General Help
---

### Post by AurolacKid on 2008-09-16
Hello.

One of my hard drives with windows crapped out and I've been trying to get some things off of it but I get an error when trying to mount it in ubuntu. 
[IMG]http://i34.tinypic.com/2e3632x.png[/IMG]

I searched some other topics on the forums but none of them seemed to help.

Any help/suggestions would be appreciated. Thanks

---

### Post by geeth on 2008-09-16
Sounds like you have to force the mount

I think the command is

sudo mount -o force /dev/sda1 /media/mountpoint

thats off the top of my head so it may be a little out and obviously the drive and mount points may differ.

---

### Post by iaculallad on 2008-09-16
Try posting your:

```
cat /etc/fstab
sudo fdisk -l
sudo blkid
```

So we could build an auto mount solution for your problem.

---

### Post by eggdeng on 2008-09-16
Open a terminal and run
```
sudo apt-get install ntfsprogs
```
which will install a program which includes a repair utility. Run the utility
```
sudo ntfsfix /dev/sdb1
```
With luck, this will repair and mount the drive.
__________________

---

### Post by AurolacKid on 2008-09-16
Ah, thank you kind sir problem solved.
Thanks to everyone else as well.

---

