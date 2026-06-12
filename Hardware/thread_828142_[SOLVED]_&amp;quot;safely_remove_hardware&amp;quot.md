---
title: "[SOLVED] &amp;quot;safely remove hardware&amp;quot; does not work, failed to force mount Lacie HDD"
date: 2008-06-13
forum: Hardware
---

### Post by dixelpixel on 2008-06-13
Dear friends,

I have gotten tons of help from this forum so far, so a general thanks to everyone reading this. I have a problem which I am aware has been discussed in several threads previously; booting an external HDD after you have used it in Windows.

My problem started when some windows process started scanning all my files. As always with Windows I was only half aware of what was going on, it seems to me that it had something to do with checking whether my student licence XP was still valid. It isn't valid I am afraid so I stopped the scanning process. I found a folder with a long title had been left on my external Lacie HDD. I deleted the folder and thought that was that. However, the problem is that now I cannot use the 'safely remove hardware' function as windows tells me there is a programme still trying to access the Lacie. I have not been able to find out what this programme is even when I use Task Manager. 

Back in Ubuntu I have attempted various force mount codes I have found, including the one that is written in the details of the error message.
" mount -t ntfs-3g /dev/sdb1 /media/LACIE -o force ".

I have pretty much given up disconnecting it from windows and what I am looking for is the mother of all force mount functions. One that really, really just forces it ;-)

All suggestions will be greatly appreciated.

Thanks,
dixelpixel

---

### Post by cdtech on 2008-06-14
In Ubuntu, use ntfsfix and that should do it for ya.

Hope this helps.....

---

### Post by dixelpixel on 2008-06-14
Hi CDTech,

Thank you for replying. I looked trough the applications I have, and the closest I could get to what you call "ntfsfix" was a programme called "NTFS Configuration Tool". I used it to enable write for both internal and external device. However this didn't change my above problem with my external HDD.
I looked trough Add/Remove applications for anything called "ntfsfix" but couldn't find anything. Then I searched Ubuntu forums for the same term without really finding any information.

Any chance you could specify where I find NTFS fix and what I do with it? All help will be received with much gratitude :-)

In advance thanks,
..dxp..

---

### Post by dacorr on 2008-06-14
Sounds like the lck file is still active on the external drive. When Windows mounts it it locks the file system which is what the safely remove bit is supposed to remove.

When you try to mount the device could you post the error message that the mount command gives you.

Dac

---

### Post by dixelpixel on 2008-06-14
Dear dacorr,

Thanks for responding, I really appreciate your help. I've attached a screenshot below.

I tried to write the same code as in the error message, only with a new folder (called "mountLACIE") as a mounting point:

sudo mount -t ntfs-3g /dev/sdb1 /home/mountLACIE -o force

I get the following error message:

-------------------
magnus@D610:~$ sudo mount -t ntfs-3g /dev/sdb1 /home/mountLACIE -o force
Password:
NTFS signature is missing.
Failed to startup volume: Invalid argument
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
---------------------


Many thanks for all help so far.

dix

---

### Post by dacorr on 2008-06-14
could you confirm that the mount point is a folder in the Home Folder?

and not somthing like

/home/dixelpixel/mountLACIE.

Additionally from terminal post the result of

sudo fdisk -l

just need to make sure that it is NTFS and that the device has not changed its letter as sda1 or sdb1

The error message is saying its not NTFS patition on the device /dev/sdb1

Dac

---

### Post by dixelpixel on 2008-06-14
AMAZING!!!

Your last effort really helped. Just had to get all details right. Well, and understand it too. Thanks thanks thanks.

Changed mount point and changed drive name. Well, seems obvious now, but I just got confused with all the different aspects of the commands.

dix.
:):):):)

---

