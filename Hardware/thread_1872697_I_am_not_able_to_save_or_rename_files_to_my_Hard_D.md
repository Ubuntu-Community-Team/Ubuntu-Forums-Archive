---
title: "I am not able to save or rename files to my Hard Disk"
date: 2011-10-31
forum: Hardware
---

### Post by pandeylavakesh on 2011-10-31
hello friends, 
 
A few days ago I installed windows 7 on my Acer Extensa 4620 laptop that already contained Ubuntu 11.10. After installing windows I'm not able to save or rename my files on a 100GB partition of HD. Actually I've made 3 partitions of my HD
 
C-30 GB for Windows 7
D-100 GB for Songs movies softwares etc
One partition for Ubuntu.
 
In ubuntu partition, there is no problem. I can save, rename and delete files from here. But while I've booted ubuntu(running Ubuntu) C and D drives are read only, but in Windows 7 everything works fine. 
 
While running ubuntu whenever I try to save or delete files it shows an error saying "Read Only Filesystem" ..

---

### Post by nothingspecial on 2011-10-31
If the shared data partition is formatted ntfs then you need to mount it read/write in etc/fstab.

or with ntfs-3g

See the ntfs section near the bottom of this page

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

be careful with your windows partition.

---

### Post by pandeylavakesh on 2011-10-31
> **nothingspecial said:**
> If the shared data partition is formatted ntfs then you need to mount it read/write in etc/fstab.

or with ntfs-3g

See the ntfs section near the bottom of this page

[https://help.ubuntu.com/community/Fstab#ntfs](https://help.ubuntu.com/community/Fstab#ntfs)

be careful with your windows partition.

actually both C(30GB) and D(100GB) drives are NTFS .

---

### Post by pandeylavakesh on 2011-10-31
Actually I'm not very expert in Linux systems so can anyone explain in details. I'm kind of new to this Linux os.

---

### Post by coffeecat on 2011-10-31
Some people are reporting that they are losing the ntfs-3g driver that comes as default in 11.10 and which provides read-write support for NTFS. Open Ubuntu Software Centre and check that you have the ntfs-3g package installed. If it isn't, install it and see if that fixes your problem.

If the problem persists, open a terminal in Ubuntu and post the output of these commands:

```
sudo fdisk -lu
sudo blkid
mount
```

You can highlight the output with the mouse, right-click and "copy" so that you can paste it into your post. 

How are you mounting the "C:" and "D:" partitions? By clicking on them in the left pane of a Nautilus file browser?

---

### Post by pandeylavakesh on 2011-10-31
> **coffeecat said:**
> Some people are reporting that they are losing the ntfs-3g driver that comes as default in 11.10 and which provides read-write support for NTFS. Open Ubuntu Software Centre and check that you have the ntfs-3g package installed. If it isn't, install it and see if that fixes your problem.

If the problem persists, open a terminal in Ubuntu and post the output of these commands:

```
sudo fdisk -lu
sudo blkid
mount
```

You can highlight the output with the mouse, right-click and "copy" so that you can paste it into your post. 

How are you mounting the "C:" and "D:" partitions? By clicking on them in the left pane of a Nautilus file browser?
 
hurrey .. I fixed it using ntfs-3g tool. 
Yup .. I think ntfsprogs is the default program in ubuntu 11.10 for the same. I saw it while installing. It first removed ntfsprogs then installed ntfs-3g. 
Again I installed ntfsprogs to check if it removes ntfs-3g and I was correct. It first removed ntfs-3g then installed ntfsprogs. 

anyways .. I served my purpose using ntfs-3g tool. 

sudo fdisk -l
sudo ntfsfix /dev/<device name>

:popcorn:

---

### Post by coffeecat on 2011-10-31
> **pandeylavakesh said:**
> hurrey .. I fixed it using ntfs-3g tool. 
Yup .. I think ntfsprogs is the default program in ubuntu 11.10 for the same. I saw it while installing. It first removed ntfsprogs then installed ntfs-3g. 
Again I installed ntfsprogs to check if it removes ntfs-3g and I was correct. It first removed ntfs-3g then installed ntfsprogs. 

anyways .. I served my purpose using ntfs-3g tool. 

Yes - I guessed that installing ntfsprogs would be the problem.

A FYI for anyone coming across this thread. In 11.10 ntfs-3g is installed by default and the version of ntfs-3g in 11.10 now includes the various utilities that were previously supplied by ntfsprogs. You do not need ntfsprogs in 11.10. Because it now conflicts with ntfs-3g, if you try to install ntfsprogs in 11.10, the package manager will remove ntfs-3g, but not before prompting you.

You do still need ntfsprogs (if you require those utilities) in Ubuntu 11.04 and before.

---

