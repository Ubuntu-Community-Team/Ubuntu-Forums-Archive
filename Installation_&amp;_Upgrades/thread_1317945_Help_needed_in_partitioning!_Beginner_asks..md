---
title: "Help needed in partitioning! Beginner asks."
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by ckop64 on 2009-11-07
Hello everybody!
I'm a noob in Ubuntu, and need your help in partitioning.
First, here is a screenshot, taken from the LIVE CD, partitioning section.

[http://img194.imageshack.us/img194/989/screenshottelepts.png](http://img194.imageshack.us/img194/989/screenshottelepts.png)

So, as you can see, I have windows 7 installed, and I'd like to keep is as my primary operating system.
I want Ubuntu 9.10 to be selectable from a list (Like grub, or something like that).
Problem is, i have Ubuntu 7.10 installed aswell, but it doesn't work. (so upgrading is not possibile). So right now I want to install Ubuntu 9.10 on the partition of 7.10, like formatting those ext3 partitions that 7.10 has, and install 9.10 on them.
But i don't know how to do that, so that i need help with.

Now, there is no list of operating systems on boot, so my system automatically boots on Windows 7.

Thanks for your help!
ckop64

**Note: **In case if you can't understand what the installer says, i translate it for you.

"This computer has multipile operating systems installed"
--colorful stripe, showing the partitions--

"where do you want to install Ubuntu 9.10?
" (option 1) Install Ubuntu 9.10 next to the other operating systems, choose from a list which one do you want to boot."
" (option 2) Use the whole hard disk"
" --this erases Windows 7 loader, and Ubuntu 7.10, installs Ubuntu 9.10"
" (option 3) You give the full details of the partitions (Advanced users only!)"
--orange stripe-- 

Hope this is enough information for you :)

---

### Post by dragonboss on 2009-11-07
You have to go to the manual config part for advanced users only (Don't be too scared by this!) and note the partition your Ubuntu 7.10 is on and select this as as "/" but Please Select The CORRECT Partition. And just to be safe back up your data first(if you haven't already done that)

---

### Post by ckop64 on 2009-11-07
> **dragonboss said:**
> Do you want to completely wipe your 7.10 or you want to kep some files?

I want to completely wipe it, i dont need anything from my old 7.10 partition!

---

### Post by ckop64 on 2009-11-07
> **dragonboss said:**
> You have to go to the manual config part for advanced users only (Don't be too scared by this!) and note the partition your Ubuntu 7.10 is on and select this as as "/" but Please Select The CORRECT Partition. And just to be safe back up your data first(if you haven't already done that)

Do you mean something like this?

[http://img442.imageshack.us/img442/5986/screenshotzr.png](http://img442.imageshack.us/img442/5986/screenshotzr.png)

**It says:**

EDIT ONE PARTITION

New partition's size in megabytes: 31914
Usage: ext3 journaling filesystem  <= before it was out of usage
Format partition? [yes]
coupling point : "/" <= there were options like /boot, /home, etc.

---

### Post by dragonboss on 2009-11-07
Yes thats it and just double check the partition is correct cos from what i see from the two pics it is on /dev/sda8
Let me know if its ok so I can mark this thread as solved

---

### Post by ckop64 on 2009-11-07
> **dragonboss said:**
> Yes thats it and just double check the partition is correct cos from what i see from the two pics it is on /dev/sda8
Let me know if its ok so I can mark this thread as solved

Ok, I'm done. Installation went fine. Restarted my PC, selected linux from GRUB.
The Ubuntu logo showed up, than black screen, no graphical interface, just bunch of white writing. It asked me to log in, so i did so. After that it is only a terminal. No error messages. 

Any idea?

---

### Post by dragonboss on 2009-11-07
Try reinstalling again by using the live cd and try removing the new installation by using the disk utility in System > Administration to delete that partition, which will them become free space and then initiating the install. This should then allow you to install Ubuntu alongside Windows.

---

### Post by ckop64 on 2009-11-08
Alright, i got what was wrong.
The installer somewhy didnt copy custom.conf. This has something to do with x.org. 
I managed to solve this by decreasing the number of the partitions on my HD and reinstalling.

Thanks for all your help. :)
ckop64

---

