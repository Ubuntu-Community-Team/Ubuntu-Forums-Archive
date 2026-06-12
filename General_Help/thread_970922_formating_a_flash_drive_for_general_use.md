---
title: "formating a flash drive for general use"
date: 2008-11-04
forum: General Help
---

### Post by capo1949 on 2008-11-04
Hi All
I recently used a 8GB flash drive for recovery of an ASUS PC 900. I now wish to reformat it for general use in transferring data between my dell and asus. In shows only a 1.3 GB in size and a fat file from its use as recovery, I would like to reformat it so as to regain my 8GB use and also rename it.
Many thanks in anticipation
Graham
 Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         701     1369022    6  FAT16

---

### Post by scouser73 on 2008-11-04
What you need is Gparted, which can be found in the repositories. Once you have installed the program, look under **System**, **Administration**, it will be called **Partition Editor**. 

Once you have formatted it, you can give it a label, visit this site for more information; [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by capo1949 on 2008-11-05
hi Scouser73,
Thx for your response
I used the GParted to obtain me 8GB. Then used disclabel to, I thought relabel the disc, duh.Formatted eo fat 32 and now the stick is not recognised on plug in, also when i try to run gparted it stars to load then disc
Thanks in anticipation 
Graham

---

### Post by shortcut144 on 2008-11-05
No expert, just a thought.  Format the drive as FAT16.  That is used more for smaller drives, such as 8GB.  You should be able to recognize it then.

---

### Post by capo1949 on 2008-11-05
Hi
Yes would like to format fat16 or ext2 but i cannot mount the device or run GParted
Graham

---

