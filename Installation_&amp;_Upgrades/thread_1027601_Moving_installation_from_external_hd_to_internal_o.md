---
title: "Moving installation from external hd to internal one"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by adam98 on 2009-01-01
Hello i have ubuntu 8.10 on an external usb disk. I want to ask if i can move this installation to my internal hard disk so as to get rid of xp. Apart from the changes on the boot loader file do i have to do anything else or i just move the files to the new partitions? Thanks for the help

---

### Post by logos34 on 2009-01-01
How are you going to copy it?  If you plan to image/clone it, then no...If you copy it with **cp -a**, then you'll have to edit the UUIDs in fstab and menu.lst.

---

### Post by caljohnsmith on 2009-01-01
If you make room on your internal drive first by deleting one or more of the partitions on that drive, you can use Ubuntu's partition editor gparted to simply copy/paste your Ubuntu partitions to the new drive. If you do that without resizing the partitions, their UUIDs shouldn't change, so you shouldn't need to update any system files. If you do decide to resize the partitions, it is possible to simply reinstate their original UUIDs after you are done resizing so that you don't have to modify any system files. If you want any details of how to do that, let me know; otherwise good luck and let us know how it goes. :)

---

### Post by logos34 on 2009-01-01
> **caljohnsmith said:**
> If you do that without resizing the partitions, their UUIDs shouldn't change, so you shouldn't need to update any system files. If you do decide to resize the partitions, it is possible to simply reinstate their original UUIDs after you are done resizing so that you don't have to modify any system files.

Actually, on a typical setup the only UUID that changes after partition resize is /swap.  But, yes, the OP could use tune2fs -u uuid to generate the same one again

---

### Post by adam98 on 2009-01-02
I am going to format the internal disk which is 40gb and I want to move my ubuntu system there. The partition where my ubuntu sits currently is 15 gb. Yes i need all the help you can suggest!

---

### Post by caljohnsmith on 2009-01-02
> **adam98 said:**
> I am going to format the internal disk which is 40gb and I want to move my ubuntu system there. The partition where my ubuntu sits currently is 15 gb. Yes i need all the help you can suggest!
OK, if you want to give the copy/paste partitions method a shot, once you've formatted the internal HDD, how about booting your Ubuntu Live CD (the install CD), go to System > Admin > Partition Editor, select your Ubuntu partition on the external drive, and do a copy/paste of that partition to your internal drive. Also copy your swap partition on your external drive to the internal drive, assuming you were using a swap partition before and not a swap file. If that all goes well, next open a terminal (Applications > Accessories > Terminal) and please post the output of:
```
sudo blkid -c /dev/null
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by adam98 on 2009-01-03
OK , thanks i will keep you update i can' t do it until next friday, since i need one working computer until then!

---

