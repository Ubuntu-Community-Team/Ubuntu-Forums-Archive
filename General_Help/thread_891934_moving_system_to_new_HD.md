---
title: "moving system to new HD"
date: 2008-08-16
forum: General Help
---

### Post by enjoy777 on 2008-08-16
hello

I have installed Ubuntu 8.04 on one of my disk it is 120 GB IDE HD. I would like to move all my system width GRUB and all my data from this HD to new HD, the new is 250 GB SATA II. Is it possible and how to do it easy? Why I want to do is because I don't want to install everything from scratch on new HD.

Any idea?

---

### Post by Victormd on 2008-08-16
Probably your best bet is to install hardy from scratch on the new HD with the same user name and password, then copy your home from the old to the new HD (or even, just copy all the files from one to the other once the install is complete overwriting everything). You will want to backup your menu.lst from the new install and once you've copied all the files, replace menu.lst and all should be Ok. Don't delete the files from your old HD until you're sure it's working.

---

### Post by colobix on 2008-08-16
You could use the program Remastersys to take a full system backup on a DVD. The program will also include an installation program on your DVD so you can just install the system over on another HD and format the old HD.

---

### Post by enjoy777 on 2008-08-16
thx for your ideas.

I don't want to create backup I want only move system from one HD to another without of needing to create DVD. I have HD with 3 partitions:
1. /
2. /home
3. /swap

and on new disk I can prepare the same and if any command exists I would like to use and copy and paste all data from partitions form old HD to appropriate partitions of new disk. After this I want to switch boot option in BIOS to boot from new disk. Is it possible?
And if yes how to create GRUB MRB sector?

---

### Post by MattBD on 2008-08-16
You can use the DD command from the command line to image an entire partition or hard drive. However, I don't think you can do that while it's mounted. You might want to use a live CD for that - I think the Ubuntu live CD can do it, or you could use Knoppix.
The syntax for it is as follows:
```
sudo dd if=/dev/hda of=/dev/hdb
```
where /dev/hda is the drive you want to copy from and /dev/hdb is the drive you want to copy to.
That will copy one drive straight onto another. To just copy one partition onto another drive, you can use something like this:
```
sudo dd if=/dev/hda1 of=/dev/hdb1
```
Or you can save it as an image of your drive rather than just copying it over to a new drive. All you need to do is pass a filename instead of a device name as the destination, like this:
```
sudo dd if=/dev/hda1 of=/mnt/hdb1/hda1_drive_image.img
```
This can be handy for backing up your system. Then to reimage the file to a hard drive, enter something like this:
```
sudo dd if=/mnt/hdb1/hda_drive_image.img of=/dev/hda1
```
Hope this makes sense!

---

### Post by enjoy777 on 2008-08-16
@MattBD

Does it copy GRUB to new disk too?

---

### Post by MattBD on 2008-08-16
> **enjoy777 said:**
> Is it copy GRUB to new disk too?

I think GRUB is normally in the root partition, unless you have a separate boot partition, so I believe under those circumstances GRUB would be copied across.
If you can plug both drives in at the same time, it would probably be easiest to just copy the whole drive image across, rather than individual partitions. As long as the target hard drive is the same size or larger than the original, it should work fine.

---

### Post by enjoy777 on 2008-08-16
thank you MattDB I am going to check how it works and what effect I will get :)

---

### Post by MattBD on 2008-08-16
Before you do that, I suggest you run the following:
```
sudo fdisk -l
```
That will tell you what hard drives are connected to your system so you can figure out which one is the source and which is the destination.

---

