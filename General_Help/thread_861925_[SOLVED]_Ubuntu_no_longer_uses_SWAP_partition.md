---
title: "[SOLVED] Ubuntu no longer uses SWAP partition"
date: 2008-07-17
forum: General Help
---

### Post by Stason on 2008-07-17
After resizing the partitions Ubuntu stopped using swap partition. In the resource manager it says SWAP 0 of 0 bytes. In partition manager there is swap partition. How to make Ubuntu to start using swap again?

---

### Post by Locutus_of_Borg on 2008-07-17
add this to /etc/fstab

/dev/sda4   none         swap    sw                   0 0

change /dev/sda4 to your swap partition of course

you can use swapon to turn it on now if you don't want to reboot

man swapon for the correct syntax

---

### Post by Rocket2DMn on 2008-07-17
The UUID of your swap partition probably changed because of the resizing, please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
We will help you set the correct UUID for swap.

---

### Post by jimv on 2008-07-17
Thats funny.  I just resized some partitions this evening, and I went and looked, and sure enough, my swap said 0 out of 0 as well.  I was able to fix it pretty easily.

Go to System > Administration > Partition Manager
Right-click on your swap partition and click 'Swapon'
Right-click on the swap partition again and click 'Information'.  It should say that the status is active, and you should also see swap space available in the Resource Manager now.

---

### Post by Locutus_of_Borg on 2008-07-17
> **Rocket2DMn said:**
> The UUID of your swap partition probably changed because of the resizing, please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
We will help you set the correct UUID for swap.

why does ubuntu use uuid?

is there a secret benefit over just using the drive labels?

seems actually worse and harder to maintain at first glance...

---

### Post by Rocket2DMn on 2008-07-17
> **Locutus_of_Borg said:**
> why does ubuntu use uuid?

is there a secret benefit over just using the drive labels?

seems actually worse and harder to maintain at first glance...

It is taking over for /dev locations because these can change between boots.  It is a real problem for some people if their hard drives are detected in different orders between boots.  Using UUIDs solves this problem, and UUIDs only become a problem if a user fiddles with the partitions (rather than doing nothing except booting the computer).  It makes more sense to deal with changing UUIDs in fstab after changing your partitions than having to deal with not being able to boot your computer when you haven't changed anything.

---

### Post by Locutus_of_Borg on 2008-07-17
ah
i wasnt thinking of external drives...i guess they do sometimes change

i have never had a problem as i only have the one drive, and anything i plug into usb is always /dev/sdb

thanks for clarifying

---

### Post by iaculallad on 2008-07-17
What displays when you issue the command below on your terminal:

```
free
```

Sometimes, if Ubuntu doesn't use the SWAP, it only means that it's using your RAM efficiently. The only time Ubuntu activates/uses SWAP is when it sees that you need more RAM for applications/processes to be executed.

NOTE: RAM is still faster than using SWAP.

---

### Post by Stason on 2008-07-17
> **Rocket2DMn said:**
> The UUID of your swap partition probably changed because of the resizing, please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
We will help you set the correct UUID for swap.

New UUID was exactly the case. Thank you.:guitar:

---

