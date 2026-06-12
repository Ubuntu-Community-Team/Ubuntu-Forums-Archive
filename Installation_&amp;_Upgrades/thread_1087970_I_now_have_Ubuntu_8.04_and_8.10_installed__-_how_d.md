---
title: "I now have Ubuntu 8.04 and 8.10 installed  - how do I delete 8.04"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by inearlygaveup on 2009-03-05
I duel boot with Ubuntu & XP
I upgraded to 8.10 and wanted to delete the old 8.04 partitions.
Deleted and enlarged the remaining partitions then could not reboot into Ubuntu or Windows.
So re-installed Ubuntu 8.04 from live CD 
Now I have Ubuntu 8.04 and Ubuntu 8.10.
How do I delete/remove Ubuntu 8.04

Can anyone help please

---

### Post by martrn on 2009-03-05
If You installed Ubuntu 8.04 to /dev/sda5  then delete the partition at /dev/sda5, however if you installed Ubuntu to /dev/sda8 then delete the partition at /dev/sda8.

The ubuntu linux version you just 'booted' into will be where the mount point is for that version and is marked by a forward hash symbol '/', only you will know if you 'booted' the 8.04 or the 8.10 version of ubuntu so only you will know what the mount point is for.

If you remove the 17.73GB partition, then everything on that partition will be lost, so make sure you move any data from that partition you might need before you remove it.

Always back up you data, before moving/deleting/resizing any partitions as changing partitions on any hard drive always carries an element of danger.

---

### Post by inearlygaveup on 2009-03-05
My startup screen says that Ubuntu 8.10 is on my /dev/hda5.
Does that mean that Ubuntu 8.04 is on /dev/hda8.

---

### Post by martrn on 2009-03-05
If your startup screen says that Ubuntu 8.10 is on /dev/hda5 and when you took the above screenshot you booted into that Ubuntu 8.10 to take the that (the above) screenshot, then

Yes that means that Ubuntu 8.04 is on /dev/hda8. 

I err guess you must of shrank one of your fat32 partitions each time to make room for the linux distributions.

---

### Post by Therion on 2009-03-05
Holy cow... 

If you want 8.10 as you sole OS, I'd do a clean install and choose to use the entire drive.  

But that's me.  Just me and just my opinion born and forged from my few years of experience which has taught me me that that is the proper way to install and OS if I don't want problems down the line.

---

### Post by inearlygaveup on 2009-03-07
taurus - attached is a print of my system after new installation

---

### Post by taurus on 2009-03-07
So you've reserved 29GB for / (root filesystem) and you are currently using 2.8GB (default installation) of it, 10%.

And if you want to know how much swap space the system reserved, just look at the output of this command from a terminal.

```
free -m
```

---

### Post by inearlygaveup on 2009-03-07
does that sound right

---

### Post by taurus on 2009-03-07
You mean the disk space?

Post the outputs of these commands.

```
sudo fdisk -lu
cat /etc/fstab
free -m
```

---

### Post by inearlygaveup on 2009-03-07
Swap space

---

### Post by inearlygaveup on 2009-03-07
yes

---

### Post by taurus on 2009-03-07
> **inearlygaveup said:**
> Swap space

So you have about 2GB of swap space.

---

### Post by inearlygaveup on 2009-03-07
> **taurus said:**
> You mean the disk space?

Post the outputs of these commands.

```
sudo fdisk -lu
cat /etc/fstab
free -m
```

ok

---

