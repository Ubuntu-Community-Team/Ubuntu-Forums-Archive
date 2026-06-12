---
title: "[SOLVED] home partition on removable hard drive"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by Miikee on 2008-12-29
I have been reading several forums about this (2-3 days), but I can only do so much reading w/o just asking the questions I need.  I've tried to make this as too the point as possible.

**I have a laptop:**
[LIST]
[*]2.8 Ghz
[*]1 GB memory
[*]100 GB HDD 
[*]300 GB HDD (removable, has to be this way... long story why)
[*]And another much slower desktop, rarely used.
[/LIST]

**Needs & plans** for computer:
[LIST]
[*]I will be the only user on both computers.
[*]Want security against file theft
[*]Be able to surf internet without huge worry of security problems
[*]Using computers to learn programming
[*]I install millions of apps to experiment with
[*]Be able to install another distro for dual booting later
[*]Want to keep linux installation on 100GB HDD
[*]Want to keep media on 300 GB HDD (& apps if that is a good idea)
[*]Want to be able to move the 300GB HDD b/t desktop & laptop
[*]Want the laptop to still be able to work w/o the 300GB HDD mounted
[/LIST]

I want to partition my 100 & 300 HDD to have 
**100GB HDD:**[INDENT]
   / ------- remaining space   
   /boot --- 200 MB
   /usr ---- 10 GB
   /var ---- 2 GB
   /tmp ---- 1 GB
   swap ---- 2 GB
[/INDENT]

**300GB HDD:**  (want to use for all media... & possibly even apps)
[INDENT] /home ---- all[/INDENT]

**Questions:**
[LIST=1]
[*]Are any of these partitions completely unnecessary or too small for what I am planning to do?
[*]Is it a bad idea to keep /home on a removable HDD?  Will it not work when I move it from the laptop to the desktop?
[*]Would it be better to keep the /home on the 100 GB and just create a custom partition for media & etc on the removable HDD?
[*]Is it a bad idea to try to keep apps on the 300GB HDD?  What partition needs to be on the 300GB HDD to accomplish this? Will just the /home partition work for this... or is another folder like /usr needed?
[*]Will the desktop be able to use the /home partition when the 300GB HDD is swapped?  Will the laptop work well w/o the 300GB HDD?
[*]Overall is this a good idea, what would you do with the drives, Please let me know your thoughts... I appreciate it.
[/LIST]

Thank you very much for helping me get this right the first time.  I had been using the 100GB HDD before I screwed it up and noticed that it may run out of space within a another year, and that I may have problems with fitting more apps on it for Linux.

Thank you again!

---

### Post by kunixos on 2008-12-29
> **Miikee said:**
> I have been reading several forums about this (2-3 days), but I can only do so much reading w/o just asking the questions I need.  I've tried to make this as too the point as possible.
**Let's get to it!**

**I have a laptop:**
[LIST]
[*]2.8 Ghz
[*]1 GB memory
[*]100 GB HDD 
[*]300 GB HDD (removable, has to be this way... long story why)
[*]And another much slower desktop, rarely used.
[/LIST]
**Pretty straight forward setup**

**Needs & plans** for computer:
[LIST]
[*]I will be the only user on both computers.
**Easily done. Just create the ONE user on each system**
[*]Want security against file theft
**I'm gonna need you to be more specific here. If you mean a firewall, then just look around for some good applications**
[*]Be able to surf internet without huge worry of security problems
**Then you chose the right distro!**
[*]Using computers to learn programming
**I would recommend KDevelop for beginners as it has a lot of GUI tools for several different programming languages. Make sure to install the build-essential package so you can compile programs**
[*]I install millions of apps to experiment with
**Make sure you keep a running list of the names of the programs you install. Be scrupulous! It'll pay big dividends when you are trying to hunt through dependency libraries later**
[*]Be able to install another distro for dual booting later
**If this is the case, think about leaving some space on your 100GB HDD for the rootfs of your 'other' distro (and as a tip for learning the ins and outs of Linux, try LFS)**
[*]Want to keep linux installation on 100GB HDD
**Definitely easy to do**
[*]Want to keep media on 300 GB HDD (& apps if that is a good idea)
**It is not a good idea to keep the applications on the external HDD. Also, it would be better if you left the /home pointer on your 100GB HDD and created a folder within your /home like /home/Files that was permanently linked to the external HDD (this is what I'd recommend so that you can move the portable from one to the other while maintaining the work-ability of the Laptop when the external HDD is not connected)**
[*]Want to be able to move the 300GB HDD b/t desktop & laptop
**See above explanation**
[*]Want the laptop to still be able to work w/o the 300GB HDD mounted
**The only way that's gonna happen is if you make a subfolder within your /home folder. Making your /home directory point to a non-connected device will cause the system to create a new /home directory and then you'll have file conflicts**
[/LIST]

I want to partition my 100 & 300 HDD to have 
**100GB HDD:**[INDENT]
   / ------- remaining space   
   /boot --- 200 MB
   /usr ---- 10 GB
   /var ---- 2 GB
   /tmp ---- 1 GB
   swap ---- 2 GB
   **Again, you'll want to add the /home directory with about 500MB or so in space**
[/INDENT]

**300GB HDD:**  (want to use for all media... & possibly even apps)
[INDENT] /home ---- all[/INDENT]
**Here's where you'd just make it an open set of folders (not specifically creating a /home folder which all the files are stored in)**

**Questions:**
[LIST=1]
[*]Are any of these partitions completely unnecessary or too small for what I am planning to do?
**Looks like a good setup. Just take a look at my suggestions**
[*]Is it a bad idea to keep /home on a removable HDD?  Will it not work when I move it from the laptop to the desktop?
**No it will not work. This is why I suggest using another folder-pointer (or more accurately a mount-point) within your home folder**
[*]Would it be better to keep the /home on the 100 GB and just create a custom partition for media & etc on the removable HDD?
**Yes**
[*]Is it a bad idea to try to keep apps on the 300GB HDD?  What partition needs to be on the 300GB HDD to accomplish this? Will just the /home partition work for this... or is another folder like /usr needed?
**To keep the applications on the 300GB HDD you'd have to mount /usr to the external HDD. Bad idea. Without the external your Laptop would be useless (unless you were running super-user apps only)**
[*]Will the desktop be able to use the /home partition when the 300GB HDD is swapped?  Will the laptop work well w/o the 300GB HDD?
**Everything should work fine if you use the external for a misc-media-type function and not the established /home directory**
[*]Overall is this a good idea, what would you do with the drives, Please let me know your thoughts... I appreciate it.
**It sounds like you have the concept down to a science. Another suggestion would be to create an internal network and put the 300GB HDD into a NAS case. This will give you networking experience as well as erase the need for moving the external drive from one computer to the next.**
[/LIST]

Thank you very much for helping me get this right the first time.  I had been using the 100GB HDD before I screwed it up and noticed that it may run out of space within a another year, and that I may have problems with fitting more apps on it for Linux.

Thank you again!

**You're welcome!**

---

### Post by tommcd on 2008-12-29
If you have /home on the external hard drive, then all your hidden configuration files will be there. When you remove the external hard drive and boot Ubuntu it will not be able to find /home and you will get errors.

It is not necessary to create a separate /boot, /usr, /var, etc. If any of those are on the external drive then you will not have those directories if you boot without the external drive.

Keep it simple.
Partition the laptop with as many partitions as you want for installing different distros. Make each one 10-12GB. Also create a swap. On the external drive make one partition and call it /data. Put all your music, videos, text files, etc in there.

The external drive will probably be /dev/sda1. You can create a mount point for it called /data when you install Ubuntu, or you can add it to your /etc/fstab and create a mount point for it later if you want. When you install another distro mount /dev/sda1 as /data, just the same as in Ubuntu. This way all distros will be able to access /data.

All distros will have a /home directory inside their respective partitions on the internal drive on the laptop. That way each distro's /home is separate and can't get mixed up.

---

### Post by Miikee on 2008-12-29
Thank you very much. Those replies were exactly answers and reasoning I needed to hear.  I will definately not be doing the external /home, except as a link.  I'm glad I asked about this instead of trying to make it work.

---

