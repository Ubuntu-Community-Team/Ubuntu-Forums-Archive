---
title: "USB Hard drive problem"
date: 2011-01-13
forum: Hardware
---

### Post by DSharma on 2011-01-13
hi guys, I am new to linux so excuse me if this ends up being a silly question/problem.. 

I have a usb disk (seagate 500gb) which is not being recognized in windows. Somehow, I did not eject it properly and now it is not being read in windows. I tried with a the backtrack CD and bt is able to read from the drive. Now, when I connect the same drive through Ubuntu (installed in the system), though the drive is mounted properly (the size is reflected correctly), but the drive data is not visible. 

What is it that I am doing wrong?

---

### Post by Ad@m on 2011-01-13
I can only guess that Ubuntu is not mounting the drive because it detects the NTFS drive has not been shut down cleanly.

Try running ntfsfix on the drive

sudo ntfsfix /dev/sdX

X = the USB drive letter

However, it is best to run chkdsk in Windows.

Check if windows sees the disk in computer management.

Right click on my computer > Manage > disk management

If so, open a cmd prompt and run chkdsk on the disk, eg chkdsk e:

---

### Post by DSharma on 2011-01-13
I have already tried the chkdsk part. Didnt work out: it says its a raw drive and cant be repaired. Will try out the other option. Thanks

---

### Post by friv_livs on 2011-01-13
also, is your drive tilted at even a slight angle to horizontal when layed on a surface?

Sometimes the read head gets at the wrong angle to see the data properly.

---

### Post by DSharma on 2011-01-15
No Luck yet. The hard drive is properly placed.

---

