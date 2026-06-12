---
title: "Mounting both internal and external USB drives from which (if any) Live CD??  HElp!"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by jfighter on 2006-09-19
Hi,

Still fairly new to Ubuntu here.  I'm trying to clone the hard drive contents of one laptop to a newer laptop I purchased.  Problem is that I don't know of a Live CD that is able to detect and mount BOTH my laptop's local C: drive AND a USB external drive containing the backup image of my old laptop.  Even using my Windows XP CD has problems because although it can see my local C: drive, it can't see any attached USB drives.  :mad: 

I tried using the Ubuntu Desktop Live CD but it couldn't mount my local C: drive (also followed forum advice about doing this but nothing worked).  Do you know of ANY linux Live CD distros that automount local C: drive and USB drives?

Thanks!

---

### Post by mssever on 2006-09-19
What is the format of the partition in question? I'm assuming that it's NTFS, given that you called it the C: drive (there's no such thing as a C: drive in Linux, just as there's no such thing as the hda1 partition in Windows). If so, the question is: to you want to write to an NTFS partition from Linux? If so, I don't know of a Live CD that will do it. Otherwise, provide details of your setup and I can help.

---

### Post by jfighter on 2006-09-19
> **mssever said:**
> What is the format of the partition in question? I'm assuming that it's NTFS, given that you called it the C: drive (there's no such thing as a C: drive in Linux, just as there's no such thing as the hda1 partition in Windows). If so, the question is: to you want to write to an NTFS partition from Linux? If so, I don't know of a Live CD that will do it. Otherwise, provide details of your setup and I can help.

Local partition has been formatted as NTFS and external USB partition is NTFS.  I have created an ISO image backup of my Win XP Pro system on an older laptop using Acronis.  This backup is now on my external USB drive and want to copy this to the formatted NTFS local drive on my new laptop.  Eventually I will run my Acronis boot CD to restore the image on my local drive.

It's strange how my external USB drive can mount but not my local drive even though both are NTFS.  I suppose I'll have to look into building a slipstreamed Windows XP rescue disc (sounds like no short task) instead unless you have other suggestions...

thanks

---

### Post by mssever on 2006-09-19
Ubuntu only has an automounter for removable drives. You'll have to manually mount your internal partitions. Assuming that your "C" drive is hda1, do this:
```
sudo mount -t ntfs -o defaults,nls=utf8,umask=007,gid=46 /dev/hda1 /mnt
```
To unmount, do this: ```
sudo umount /mnt
```

---

