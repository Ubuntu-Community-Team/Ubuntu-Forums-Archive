---
title: "Having trouble dual booting Win 7 and Ubuntu"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by cujo_77 on 2009-08-11
I have a PC that I already have Win 7 installed on one partition (boot and software partition), then I have a second partition (Storage partition).  Last I used GParted to make a third 30 GB parition which I wanted to install Ubuntu 9.04.  The problem is when I get to step 4 "prepare disk space," I am having trouble getting Ubuntu to install on the 30 GB driver i planned.  I have dual booted Win XP and an older version of Ubuntu, but I am having trouble with 9.04.  With Windows I usually just have to point the installer to a partition and is installs from there.  I have tried formatting the partition in NTFS and EXT3 but I still am having trouble.  I have included a picture showing my HDD and partition set up and  any help would be appreciated.

---

### Post by Moop on 2009-08-11
If your going to create the partition first you'll need to use the manual partition method. It might be easier to just delete the partition you want Ubuntu on and then during install tell it to install to the unused space.

---

### Post by Yvan300 on 2009-08-11
Take the 30 gb partition and format it, and instead of formatting to a primary partition, turn it into an extended partition. Then divide that extended partition into 3 parts.

1. For root, this is where ubuntu will be installed.(Give it 10 gb)
2. For your home partition where all your personal documents will be saved.(Remaining space)
3. For the linux swap partition which is used as swap space.(twice the amount of ram you have)

Once you have done this, choose the manual option which is (advanced) in brackets and it will ask you to assign the mount points. Assign no 1 (/), which stands for root, no 2 (home) and no 3 (linux swap) and it is pretty straight forward from then on.

Good luck!

---

### Post by roharme on 2009-08-11
I would suggest different way.
 
Log in to Windows 7
 
Now create two partitions One for Root and Other for Swap.
 
Just partition dont format.
 
Now reboot and install Ubuntu.
 
In partition management, select manual.There just select the partitions you made in Windows 7 (root and swap).
 
You are done.
 
This could be it.

---

