---
title: "swapping to new Hard drive."
date: 2010-04-28
forum: Hardware
---

### Post by Phillk on 2010-04-28
Hi All,

I made the move to Ubuntu with great success. I am dual booted with Windows XP and Ubuntu. 

I need to migrate to a larger hard drive.  Is there a way to to make this move without having to reinstall individual OS and programs?

I have a copy of XP that is actually working:confused:, and I don't want to lose my Ubuntu set up either. 

Thanks,  Phill K

---

### Post by 2hot6ft2 on 2010-04-28
Welcome to the forum.

Clonezilla should be just the ticket.
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by prshah on 2010-04-28
> **Phillk said:**
> 
I need to migrate to a larger hard drive.  Is there a way to to make this move without having to reinstall individual OS and programs?

The following commands are very dangerous and should be used with extreme care and attention.

Attach your second (larger) harddisk drive to your computer when off. For the purpose of this post, /dev/sda refers to your old (small) HDD, and /dev/sdb your new (larger) HDD.

Boot off a live CD. Ensure all partitions in your drives are unmounted.  Open a terminal (Applications-Accessories-Terminal). Unmount any active swap partitions with the command ```
 sudo swapoff -a
```

Find out the correct device names of your installed HDDs. Use the command ```
sudo fdisk -l
``` to list attached harddrives and information thereof.

To copy everything from your old hdd (Eg, sda) to your new hdd(Eg, sdb) use the command```
sudo dd if=/dev/sda of=/dev/sdb bs=32k
``` Copying will take a longish time. IF YOU MAKE A MISTAKE AND REVERSE THE HDD NAMES OR IF/OF PARAMETERS, YOUR NEW BLANK DRIVE WILL BE COPIED TO YOUR OLD DRIVE, in essence wiping out all your data, INSTANTLY.

At the end of the copying, your new HDD (sdb) will contain all data and partitions of the old HDD (sda). The larger HDDs extra space will be unpartitioned.

When copying is complete, shutdown, remove your old drive, plug in the new drive in it's place (Eg using the same SATA port) and reboot. You should now be able to use your programs and data without any special activities.

When you are satisfied everything is fine, you can extend partitions to use up the unused space in your new HDD.

Please post back if you have any doubts. Since this is a very risky operation, I suggest you wait for someone else to confirm these steps in case I have made a typo or so.

---

### Post by oldsoundguy on 2010-04-28
I use EZGig II from Acronis.  (works on all operating systems) make the old drive master and hook the new drive as slave.  Boot to the EZGig cd and follow the instructions for cloning. Make sure you include all hidden files.

NO damage will happen to the C drive

To test, reverse the jumper set up on the drives and boot to the new drive.

Hold on to the old drive until you are 100% sure the new one has everything you want. and ESPECIALLY if you go to the new drive and change partition sizes.

---

### Post by Phillk on 2010-05-01
Wow! thanks for the response.

Unfortunately, life struck and this project has been put on hold.

The oil change on the car ended up including a trip to the tire shop.

I guess you can say I spent money on discs, just big ones.

Thanks again.
Phill K

---

