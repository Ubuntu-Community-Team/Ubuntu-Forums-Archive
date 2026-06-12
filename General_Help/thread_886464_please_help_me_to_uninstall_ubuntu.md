---
title: "please help me to uninstall ubuntu"
date: 2008-08-11
forum: General Help
---

### Post by pythoran on 2008-08-11
hello

 thank you very much for this forum it's really helping me to resolve many problems, i got a problem with my hp laptop i have installed ubuntu on it but i forget to keep windows partition so i formated all the partition and use it just for ubuntu what i'm looking for is how could i reinstall windows again because when i boot with win xp cd it says that windows didn't detect any hard disk it's normal because windows doesn't recognize linux file system please help me to formatthe hard disk in order to install windows first and than ubuntu

thank you very much

---

### Post by jocko on 2008-08-11
Windows should see the hard drive even if it can't recognize the file system on it.
But it may be that your windows cd does not contain the proper drivers to recognize the ata or sata chipset on your motherboard (If you have an old os (=XP cd without service packs) and new hardware (= less than 7-8 years old) this usually happens pretty often).
In that case you need to download the drivers from your motherboard or chipset manufacturer and make sure they are loaded before the windows installer looks for hard drives. Or get a windows XP sp3 cd and hope the drivers are integrated in the updated installer...

---

### Post by Ryadt on 2008-08-11
> **pythoran said:**
> hello

 thank you very much for this forum it's really helping me to resolve many problems, i got a problem with my hp laptop i have installed ubuntu on it but i forget to keep windows partition so i formated all the partition and use it just for ubuntu what i'm looking for is how could i reinstall windows again because when i boot with win xp cd it says that windows didn't detect any hard disk it's normal because windows doesn't recognize linux file system please help me to formatthe hard disk in order to install windows first and than ubuntu

thank you very much

Was XP the default OS on the laptop?

---

### Post by pythoran on 2008-08-11
thank you very much it seems to be the solution because no one has told me that before i'm going to buy one now hoping it can help me, thank you again i will tell you if it works 
selvatino
@
hotmail
com

---

### Post by pythoran on 2008-08-11
yes it was the default os

---

### Post by lisati on 2008-08-11
Some laptops come with a recovery DVD. With the recovery DVD that came with my laptop, it's possible have a partition available for use with Windows, and have the recovery process restore the partition to what would have been an "out of the box" state, complete with all the correct drivers.

---

### Post by pythoran on 2008-08-11
indeed but as a donkey i alwyas told the os to ask me later about the dvd restore till i format the pc so i have no dvd restore now i'm burned

---

### Post by pythoran on 2008-08-11
thank you for every one trying to help me it's not the same mood on the other ubuntu forums

---

### Post by forger on 2008-08-11
Maybe I'm wrong, but at least try this before buying anything :)

You can use gnome partition editor (gparted) to format it and delete the partition

1) Put in your Ubuntu Live CD
2) Reboot
3) If your BIOS is set-up correctly, it will boot up from the CD
4) Start Ubuntu as "Try Ubuntu without any change to your computer"
5) The partition editor is in menu System > Administration > Partition Editor
6) On the upper right corner, you choose your device (hard disk drive)
Find your hard disk that you want to delete its partitions
7) Now, in the main area of the program, you see the partitions of the hard disk you chose, right-click on the one you want and Format it or delete it
8) [COLOR="Red"]**BE SURE YOU SELECTED THE RIGHT PARTITION / HARD DRIVE!!**[/COLOR]
9) Click Apply to apply the changes - Let it finish
10) Go to System > Quit > Restart
11) Take out the Ubuntu CD, put in the Windows XP CD, you should see the hard drive

---

### Post by Ryadt on 2008-08-11
Go in Bios. Look for flash modules and disable it. Then look for ata drives and switch from ahci to ata.

---

### Post by pythoran on 2008-08-11
forger if it works i will kill my self hahahaa it seems to be very simple, thank you brother i will try it thank you ryadt i will do what you told me please pick a look time to time to this thread so you will see if it's resolved thank you it's kind bye

---

### Post by forger on 2008-08-15
pythoran, if it couldn't detect it, it means that either you use a SATA hard drive that windows xp cannot find a driver for, or try creating ntfs partition on the hard drive now using Partition Editor, you can delete it from the windows xp installer afterwards

---

