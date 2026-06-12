---
title: "Install on Mac OS X with XP"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by esalnoj on 2009-03-21
Any recommended install guides for ubuntu onto Mac OS X?

How do you partition the main hard drive in this Mac OS?

Will the ubuntu grub allow Windows XP to be installed after it, which was installed next to Mac OS X?

Many thanks

Esalnoj

---

### Post by SladeHN on 2009-03-21
Hello.
I too, own a Mac. I love it! Isn't it the best?
Anyways, I had Vista Ultimate installed via bootcamp, and after it kept crashing, I decided to put Ubuntu over it! It worked great. Considering your XP partition was probably created with bootcamp, it will not allow you to create another partition that way.
If I were you, I would use Disk Utility (Macintosh HD> Applications> Utilities) and make a partition that way, and install Ubuntu on that.
Now, about the startup menu, I'm assuming since you have Windows already installed, you know you press the option key during startup. Well, from my experience, it will come up with three options:
Macintosh HD
Windows
Windows

Now, maybe if you fool around with it, you can figure out how to change the partition names. I never really bothered to though, because since your XP partition was already made, it is the partition to the right of you Macintosh HD. The Ubuntu partition will be to the right of your XP partition. 
If I did not answer this correctly or if you have any questions or anything, please reply.

---

### Post by esalnoj on 2009-03-21
I want to install ubuntu next to Mac OSX, then install XP next to ubuntu.

---

### Post by SladeHN on 2009-03-21
No, not a good idea.
You should install XP on a partition the size you want both of them to be, and then install ubuntu on it.

---

### Post by esalnoj on 2009-03-21
In that case, I would want to: 
first partition the drive into two, format and install XP on the new partition 
then split the second partition and install ubuntu?

---

### Post by rienholt on 2009-03-21
I have done several of these. There is no need to use BootCamp. I always do it this way.

1. Format the entire drive into three FAT32 partitions with disk utility.
2. Install OSX to the first partition. (Repartition it to HSF+ or which ever one you want to use.)
3. Install XP to the third partition. It MUST be in the last partition on the drive or it will not boot. (Format to NTFS if you want.)
4. Install rEFIt. ([http://refit.sourceforge.net/](http://refit.sourceforge.net/))
5. Install Ubuntu to the center partition making sure to install GRUB to the Ubuntu partition and *NOT* HD0.

Everything should be ship shape with rEFIt as the graphical boot manager. You can customize GRUB to skip the menu.

---

### Post by esalnoj on 2009-03-22
How do you tell Grub where to install to? 

I did not see an option in the install process for "Grub location", only guided setups for where to put ubuntu OS.

---

### Post by esalnoj on 2009-03-31
Any experience with Virtual Box being used to install XP and ubuntu?

---

### Post by esalnoj on 2009-04-20
Solved. Thanks all.

I was just being ignorant and not searching the threads for the topics in last two posts.

---

