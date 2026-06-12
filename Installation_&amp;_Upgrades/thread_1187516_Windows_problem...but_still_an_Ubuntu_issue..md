---
title: "Windows problem...but still an Ubuntu issue."
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Ryupower on 2009-06-14
Hello, I've been a long-term user of ubuntu all the way back to the Hoary Hedgehog release. But I have an issue I haven't dealt with before.

I'm trying to install (K)Ubuntu on one of our Windows machines, which dual-boots windows 2000 and XP. Well, 2000 we never use anymore, nor does it work with all the drivers and all.

Assuming that the 2000 is on a different partition, I go on the typical 'advanced' options for partitioning. To my surprise there is only one NTFS partition, and it has both Windows XP and Windows 2000 on it.

My question is how I can get rid of the Windows 2000, in order to use the emptied space to install the new (K)Ubuntu.

Thanks y'all!!!
-R

---

### Post by presence1960 on 2009-06-14
> **Ryupower said:**
> Hello, I've been a long-term user of ubuntu all the way back to the Hoary Hedgehog release. But I have an issue I haven't dealt with before.

I'm trying to install (K)Ubuntu on one of our Windows machines, which dual-boots windows 2000 and XP. Well, 2000 we never use anymore, nor does it work with all the drivers and all.

Assuming that the 2000 is on a different partition, I go on the typical 'advanced' options for partitioning. To my surprise there is only one NTFS partition, and it has both Windows XP and Windows 2000 on it.

My question is how I can get rid of the Windows 2000, in order to use the emptied space to install the new (K)Ubuntu.

Thanks y'all!!!
-R

Boot the Ubuntu Live CD and choose Try Ubuntu without any changes. When the desktop loads open a terminal and run ```
sudo fdisk -l
```
Post the output here. That sounds like a bad dream, 2 OS can't be on the same partition unless it is wubi or virtualization( but it wouldn't show like you said it did)! Let's see what you have.

---

### Post by DemonBob on 2009-06-14
You can have multiple installs of windows on the same partition as long as the windows folders are named differently. With your setup i suspect you have a WINNT folder and a WINDOWS folder on the root of your C: drive. 

If you open your boot.ini file, usually a hidden file on the root of your C: drive it should tell you which is which. Then all you have to do is boot into the OS you want to keep, and delete the other OS's Windows/WINNT folder. 

You best bet would be a clean install of everything though...

---

### Post by presence1960 on 2009-06-14
> **DemonBob said:**
> You can have multiple installs of windows on the same partition as long as the windows folders are named differently. With your setup i suspect you have a WINNT folder and a WINDOWS folder on the root of your C: drive. 

If you open your boot.ini file, usually a hidden file on the root of your C: drive it should tell you which is which. Then all you have to do is boot into the OS you want to keep, and delete the other OS's Windows/WINNT folder. 

You best bet would be a clean install of everything though...

Thanks for the info DemonBob. I didn't know that was possible with Windows. I have done it with different versions of MS Office by naming the install folders differently.

I can't imagine having multiple Windows on a machine, a lot of times one is too many...LOL

---

### Post by AoSteve on 2009-06-14
I've actually had to do this before on a windows 98 machine.   If you install the newer version of windows into a different folder, like "Windows2000" compared to "Windows"  it is possible.  The programs won't be installed on both OS's but they'll use the same program files folders.   

I actually had to install 2000 on a windows 98 (first edition) install to get my clients files off of the old machine.  The original windows 98 CD didn't have the drivers to support flash disks and windows 2000 did.  Since it had no way to connect to the internet, I installed win2k into a directory called "2000".    :)

As DemonBob said though, the best thing is a full swipe on the drive.  Running two different versions of windows is possible, but it is never a good thing! LoL

You could do like DB said, erase the contents of the "unwanted" OS's folder and do a defrag.   You may be able to resize the partition and install ubuntu that way however.  May be worth a shot to you.  Just remember...  The swap file from the unwanted OS must go, and don't delete the one you want to keep LoL.

---

### Post by Ryupower on 2009-06-14
hahaha. Thanks for the info, guys!
I'm gonna delete the right folder...I'm definitely not swiping the drive as it's got valuable data and memories on it. In fact, I'd prefer to install Ubuntu in a way that can absolutely NOT harm the XP partition...

---

### Post by AoSteve on 2009-06-15
Thing I recommend doing?    Buy yourself an external drive...   The way this machine is setup, if vista crashes, I reinstall and vwala.   I can get my backup restored in about 25 minutes (that dang drive takes a while LOL).   No need to reinstall my school software or my Office 07 Student Edition.   

You could copy everything you want over to the external and reinstall with an xp partition and an ext partition for linux.   I think that'd be the easiest thing to do.   If you don't have your XP CD or the XP key, there's ways to find a disc and getting your key is as easy as getting into your registry for a bit.  I lost my XP home CD and copied a friend of mines the other day.  I have my key, but you could find it if you have your OS running.    

I right now have a VBox with my home copy installed and updated just to make sure it worked with his disc.   Most of the XP discs are the same, just the key is different.   I don't like illegal software at all, so by all means necessary.  Try to get your information and get your stuff onto an external.  The most important part, if you have a laptop, you can take your stuff wherever you go!  :)   I got all my pictures and videos on my 250gb and just have to plug it in to see them! :)

---

