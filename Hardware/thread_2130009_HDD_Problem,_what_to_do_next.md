---
title: "HDD Problem, what to do next?"
date: 2013-03-28
forum: Hardware
---

### Post by safarin on 2013-03-28
Hi... 

After updating my ubuntu 12.04.. In this morning, when I open my laptop.. I cannot go inside my operating system (dual-boot, Win 7 & Ubuntu 12.04) just got stuck at the ubuntu logo and windows logo.

I run memtest86+ and pass without error, then I use live-CD (ubuntu live cd) as an option to backup and retrieve my data from HDD but failed to open the hard disk partitions. As I used to check the HDD using Disk Utilitiy in the live-CD, I got two warnings:

1. Reallocated Sector Count
2. Current Pending Sector Count

So, what I really need to do next? I really need my previous data on my hardisk. Is my hard disk corrupted? Can it be save as well as the data??

My condition: Stress!!! hahaha...

---

### Post by carl4926 on 2013-03-28
Probably not good. My guess is bad sectors (not that unusual in itself)

Try getting Parted Magic which will boot using only your RAM (obviously you will need another computer to get it and burn it)
Then see what you can access, maybe see if the Partition Editor (Gparted) picks everything up

---

### Post by safarin on 2013-03-28
Thank you carl4926... I will try as you recommend.. and will update soon..

---

### Post by carl4926 on 2013-03-28
In Gparted, assuming it reads the HD OK, you can select partitions and 'Check' them.

Do you have a backup? Because if the HD is on it's way out, it can actually be harmful the more times you try using it.

---

### Post by safarin on 2013-03-28
> **carl4926 said:**
> In Gparted, assuming it reads the HD OK, you can select partitions and 'Check' them.

Do you have a backup? Because if the HD is on it's way out, it can actually be harmful the more times you try using it.

Right now, I downloading the "parted magic", I already use gparted in ubuntu live-cd but only can open two partitions (I have 3 partitions).. the last partition and the most important partition cannot be opened. Maybe use Gparted using RAM (parted magic) will have another outcome...

I do not have backup just now.. That's why I really need to get inside the "last partition" to make a backup, which contain the most valuable files. :(

---

### Post by safarin on 2013-03-28
Thank you carl4926.. looks like this is the end of my hardisk.. 

Gparted failed to detect, the grub is also gone.. as you said before.. it will be harmful.. yes it is...
Anyway, thanks for your help....

---

### Post by carl4926 on 2013-03-28
Keep checking back here in case someone else has ideas

---

### Post by Mark Phelps on 2013-03-28
If the partition containing the data was NTFS, and you're willing to spend a little money -- read on:

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by safarin on 2013-03-28
Thanks Mark Phelps,

I already take off my hard drives as external hardisk.. I also try using TeskDisk of open source software as an option.. After run through the test, no partition were found in that hard disk (that's mean I don't see any data left).. I will try to use your method to know either my data already gone or it still there.. Thanks for your suggestion.

---

