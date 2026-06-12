---
title: "Ubuntu 9.10 &quot;No root file system defined&quot;"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Soundler on 2009-10-31
Okay, so I have Dell Inspiron 1520 laptop. There's Windows XP installed on it. 
I downloaded the image, burned it on a cd, rebooted and went through installation. When I reached step #5 - drive partitioning I faced a trublesome issue. I split 1 of my partitions into two. When selected one of those I got "No root file system defined. Please, correct it in the partitioning menu" error . I tried selecting other partitions, but got the same error.
Maybe I should try installing Ubuntu 9.04 or something ? Any ideas ? Thanks in advance :)

BTW, I'm a complete newbie in this

---

### Post by Hot Sauce on 2009-11-05
I am also trying to dual-boot Ubuntu 9.10 (but with Windows 7 instead of XP) and I'm getting the same error. I created three partitions with GParted Live CD: one NTFS for Windows 7, one NTFS for sharing files between Windows and Ubuntu, and one EXT3 for Ubuntu.

Can anyone help us?

---

### Post by Mark Phelps on 2009-11-05
Soundler:

When you split your partition, did you create a second one?  If so, was it formatted FAT32 or NTFS? IF so, that's your problem because ubuntu can't be installed to those partitions.  Boot with the Ubuntu LiveCD and change the partition to Ext3 format.

Hot Sauce:

Yours is NOT the same problem -- very different Windows OS with very different partitioning scheme.  Please start your own thread on this.

---

### Post by kio_http on 2009-11-05
Select manual partition scheme and choose mount option for your partition where Ubuntu is to be installed as "/" without quotes

---

### Post by dhavalbbhatt on 2009-11-05
You have to format the partitions that you created to either ext3 (default for Jaunty) or ext4 (default for Karmic). Once you do that, you should be able to load the main OS.

---

### Post by yoghurt on 2009-11-05
I don't think you even need to do that before the actual installation - when you click on the "advanced" during the installation process you'll be able to set up the partitions & file systems.

Sorry if stating obvious :)

---

### Post by Kurt R on 2010-04-01
Hello

I am getting this error when trying to install Ubuntu with the "From Within Windows" option.  And as it states to try partition manager to fix this I can't get to that function.

The Windows part of the install process had a few quirks in it, I kept having this window poping up saying "No Disk Error" 

I little info about my system MSI main board, P4 2.5 gHz, 2gbs RAM,  SIIG Sata controller with 2 320gb Maxtors (drive 0 boots Win XP),
Promise TX133 IDE controller with 2 other HDs on it, LG DVD burner and TDK CD burner.   

Kurt R

---

