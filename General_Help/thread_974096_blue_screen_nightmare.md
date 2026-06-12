---
title: "blue screen nightmare"
date: 2008-11-07
forum: General Help
---

### Post by bigdave565 on 2008-11-07
windows xp has been totally minced to the result of

STOP: c000021a [fatal system error]

the windows login process system has terminated unexpectedly with a status of 0xc0000005 (0x00000000 0x00000000).

the system has been shut down


this happens on every load, and under every mode in F8

someone somewhere else said ubuntu can be used as an alternative os but how can i get get it to load without any programs??

have downloaded the latest version and put it on disc


any help will be much appreciated

---

### Post by Paul41 on 2008-11-07
Put the CD in and boot the computer. It should boot off the CD and go to Ubuntu. If it doesn't you need to change your BIOS setting to check the CD drive before booting.

---

### Post by bigdave565 on 2008-11-07
ahh k i'll try n do that, ta

---

### Post by bigdave565 on 2008-11-07
k, ive got ubuntu up and running. is there any way i can access all my files?? 

it says it is unable to mount the volume. would the command line it says: mount -t ntfs-3g /dev/sda2 /media/disk -o force

put all this data into ubuntu?

---

### Post by bigdave565 on 2008-11-07
also, i i install ubuntu fully, would this data be erased or will it still all be present??

---

### Post by Paul41 on 2008-11-07
> k, ive got ubuntu up and running. is there any way i can access all my files??

it says it is unable to mount the volume. would the command line it says: mount -t ntfs-3g /dev/sda2 /media/disk -o force

put all this data into ubuntu? 

Are you sure the partition your data is on is sda2? In the terminal type the following to see what drives you have.

```
df
```

> also, i i install ubuntu fully, would this data be erased or will it still all be present?? 

It depends on how you install it. If you choose to dual boot your old data will not be lost. Just be careful to not format the entire drive when setting up the partitions.

---

### Post by bigdave565 on 2008-11-07
df informtion doesnt say sda2 anywhere on it. i want ubuntu to put all my windows data onto an external hard drive, and then im going to fully format the computer as im sure i had a bad virus, then transfer all my personal files back onto the hard drive but only the ones that definately wont be attacking the system!

At the install step 4 there are 3 options,i presume to keep the files i need to use guided - use the largest continuous free space or manual?

---

### Post by ciscosurfer on 2008-11-07
You need to first determine exactly which drive and/or partition your Windows OS resides.  Before you do anything else, post the output of```
sudo fdisk -l
```

---

### Post by Paul41 on 2008-11-07
Sorry, it should have been fdisk as ciscosurfer suggested instead of df

---

### Post by Paul41 on 2008-11-07
This may be helpful for you also.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by bigdave565 on 2008-11-08
Upon booting ubuntu this morning, with the hard-drive plugged in, the hard drive which was unmountable now can be accessed. Dont know what changed but im happy.

just hope it all transfers accross ok

thanks everyone

---

