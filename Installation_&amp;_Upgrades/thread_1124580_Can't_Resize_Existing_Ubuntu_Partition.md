---
title: "Can't Resize Existing Ubuntu Partition"
date: 2009-04-13
forum: Installation &amp; Upgrades
---

### Post by sheepo on 2009-04-13
I am currently dual booting UBuntu with win XP on my Dell Optiplex PC, I really like it. The problem is that I am running out of space on my ubuntu partition and I need to resize and so when I go to to try and resize the existing xp partition on my Ubuntu Live CD, it won't let me and says "NOt Enough Disk Space" or something along the lines of that but the thing is that I have over 20gbs free on the XP partition. Do any of you guys know how to get passed this so I can resize my Ubuntu partition?

Thanks

John

---

### Post by sheepo on 2009-04-13
I also forgot to note that, the pc is a Dell Optiplex GX270 and it has a 30gb hd, and 512mb of ram and a 2.0ghz processor. Oh and I resized the partiton two times before

---

### Post by silentrebel on 2009-04-13
The best program to use for what you are doing is gparted (as you may know).  The liveCD should have all the packages you need, but just in case, open a terminal and type the following:

sudo apt-get update
sudo apt-get install gparted ntfsprogs

-Now open gparted (sudo gparted) (make sure you backup anything important you may have on either of your partitions in case anything goes terribly wrong (though this is not normally the case)).  
-Select the right hard disk.  
-You should see a list of your partitions.  It seems that upon installing Ubuntu an extended partition is created in which your filesystem and your swap are created.  Right-click on the linux-swap partition and select the swap-off option.  This unmounts it so that we may make changes to the extended partition of which the filesystem is a child.
-Right-click the Windows partition and select Resize/Move and resize it as desired in the dialogue box.
-Now right-click the extended Ubuntu partition (the one that contains the two sub-partitions) in the tree-view and select Resize/Move.  Make the changes you want to make.  We need to do this first to make room for the Ubuntu filesystem partition within its parent's boundries.  
-Now right-click your Ubuntu filesystem partition in the extended partition, select Resize/Move and make the desired changes.
-Now review everything and apply changes.  It may take a while......
Good luck
Let me know if you have problems...  or if it works...
**_Don't forget to read Penguin Guy's post below!_**

---

### Post by Penguin Guy on 2009-04-13
Before you do the above steps boot into Windows and run the cleanup utility then the disk fragmenter. Also remember to always shrink partitions from the right. And as silentrebel said; back up your data.

---

### Post by sheepo on 2009-04-13
Ok I havea problem and its when I type in 

"sudo apt-get gparted ntfsprogs"

it says "E: Invalid operation gparted"

Do any of you know what this means?

---

### Post by sheepo on 2009-04-13
Ok so I was able to finally get into gparted and when I resized the Xp partition and clicked apply it said after a little it that an error has occurred. ANy of you guys know what to do? 

I'm starting to wonder if I should just complete write over the XP partition, and just get the nescessary/important files off of there

---

### Post by silentrebel on 2009-04-13
I'm sorry about the command.  I forgot, at first to insert the install command between apt-get and gparted...  I am glad you figured it out.  
Unfortunately, I do know really know what the problem could be.  The only possibility that crosses my mind is the fact that you may have hibernated your last XP session.  That *may* cause a problem.   
Anyone else?  Sorry
What is the exact error message?

As for switching completely to Ubuntu, just make sure that is what you want to do.  How long have you been using this OS?  Better to wait and make a calculated decision if you can; though I have to admit Ubuntu is pretty darn sweet (never really liked coffee though)...

---

### Post by Penguin Guy on 2009-04-13
Have you tried defragmenting as suggested above?

---

### Post by sheepo on 2009-04-13
thasts ok about the command, so here is the error 

real resize  00:00    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
ERROR(95): Opening '/dev/sda1' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.

Oh and I remembered that the last time I used the partition/XP I had to hard shut off because it froze

---

### Post by silentrebel on 2009-04-13
Okay so reboot in Windows, if it does not run chkdsk itself you can do it from the run dialogue (it may ask you to schedule it for next start-up, in which case you'll have to reboot again into Windows and let it automatically do chkdsk).  Then return to Ubuntu and follow the steps described above...
Let us know...
I hope that works.

---

### Post by sheepo on 2009-04-13
Thanks soooo much, got it working, Ubuntu is currently re-installing because of some problems, so its doing that, but all is well cause I was able to back up files.  So again thank you 

John

---

