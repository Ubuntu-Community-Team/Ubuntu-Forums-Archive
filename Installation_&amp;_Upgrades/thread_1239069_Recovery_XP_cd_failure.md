---
title: "Recovery XP cd failure"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by odiear3rd on 2009-08-13
I lost xp pro it would not bring up the desktop. Iued to recovery cd and itt went all the way to the stat of wins then error message came up that it could not see any disk installed. I did this several times to no avail. Can anyone tell me what is going on ??

---

### Post by mikewhatever on 2009-08-13
It seems that something is wrong with the Windows partition. Do you think it is related to Ubuntu at all?

---

### Post by odiear3rd on 2009-08-13
It was never partioned w/ Kubuntu. I installed kubuntu only after all attempts to recover XP failed. I did this to see if my HD died. Kubuntu works just fine. I want to Partion Xp and Kubuntu. Anyone know how this is to be done??

---

### Post by Mark Phelps on 2009-08-13
> **odiear3rd said:**
> I lost xp pro it would not bring up the desktop. Iued to recovery cd and itt went all the way to the stat of wins then error message came up that it could not see any disk installed. I did this several times to no avail. Can anyone tell me what is going on ??

That's really weird because recovery CDs are supposed to just plain work.  One of the common problems with restoring XP is that the earlier versions (prior to SP 3) often did not contain drivers for SATA controllers, so when you booted from the XP CD, it failed to see the SATA drive.

But, I would think that, if the machine came with XP preinstalled, and it already had a SATA drive, that the drivers would be incorporated into the recovery CD.

---

### Post by raymondh on 2009-08-13
I may have understood your post wrong .... are you using the original XP install disc or the OEM supplied recovery disc?

When you installed Kubuntu, did you erase the XP recovery partition by accident?  

Can you access a terminal and post back output of

```
sudo fdisk -l
```


Raymond

---

### Post by odiear3rd on 2009-08-13
This is the report:





oar3rd@oar3rd-desktop:~$ sudo fdisk -l
 
 Disk /dev/sda: 80.0 GB, 80026361856 bytes
 255 heads, 63 sectors/track, 9729 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 
 Device Boot Start End Blocks Id System
 /dev/sda1 1 2622 21061183+ 83 Linux
 /dev/sda2 9332 9405 594405 5 Extended
 /dev/sda3 * 9406 9729 2602530 83 Linux
 /dev/sda5 9332 9386 441756 82 Linux swap / Solaris
 /dev/sda6 9387 9405 152586 82 Linux swap / Solaris
 oar3rd@oar3rd-desktop:~$

---

### Post by raymondh on 2009-08-13
> **odiear3rd said:**
> This is the report:





oar3rd@oar3rd-desktop:~$ sudo fdisk -l
 
 Disk /dev/sda: 80.0 GB, 80026361856 bytes
 255 heads, 63 sectors/track, 9729 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 
 Device Boot Start End Blocks Id System
 /dev/sda1 1 2622 21061183+ 83 Linux
 /dev/sda2 9332 9405 594405 5 Extended
 /dev/sda3 * 9406 9729 2602530 83 Linux
 /dev/sda5 9332 9386 441756 82 Linux swap / Solaris
 /dev/sda6 9387 9405 152586 82 Linux swap / Solaris
 oar3rd@oar3rd-desktop:~$

Windows cannot read into ext file format.  
I do not see the standard NTFS recovery partition for windows.
To dual-boot with XP, you need to create an empty/unallocated space and then allow windows to format/install on it.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

What is on sda1?  I also see a big gap between sda1 and sda2 ... is that empty space?  Also, why 2 swap (sda5 and sda6).

When you are able to install windows, remember that it will overwrite the bootloader.  You just have to [restore grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Good luck.  Back up your files.

Raymond

---

### Post by odiear3rd on 2009-08-13
let me backup and start when this problem 1st started. I began to have a loud fan noise at startup. I would let it run for 2 mins and shout down and reboot and the noise would go away This went on for about 2 weeks. I though it was the Heat sink fan. Later I found out it was my PSU fan going bad. Then Wins crashed and I could not load the desktop display. I tried to restore w/ the recovery cd. This failed several attempts. I though the HD had died. So I decided to install Kubuntu to see what was going on. Kubuntu installed w/ no problems., except it is a 2006 version. I ordered the newest version to be sent to me by mail. Now I am trying to see  how I can get Wins XP reinstalled. I think a was told that the weakest of the PSU might be the bad boy in this game. I appreciate all the help I can get w/ this problem. :confused:

---

### Post by odiear3rd on 2009-08-13
> **raymondhenson said:**
> Windows cannot read into ext file format.  
I do not see the standard NTFS recovery partition for windows.
To dual-boot with XP, you need to create an empty/unallocated space and then allow windows to format/install on it.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=3)

What is on sda1?  I also see a big gap between sda1 and sda2 ... is that empty space?  Also, why 2 swap (sda5 and sda6).

When you are able to install windows, remember that it will overwrite the bootloader.  You just have to [restore grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Good luck.  Back up your files.

Raymond

Thanks for your help. I only allowed (sda1) 20gb for Kubuntu. Empty space (sda2) 60gb was saved for wins.  I have a 80gb HD. 5&6 sda are unknown.  Hope this helps. (see other post)

---

### Post by odiear3rd on 2009-08-25
> **Mark Phelps said:**
> That's really weird because recovery CDs are supposed to just plain work.  One of the common problems with restoring XP is that the earlier versions (prior to SP 3) often did not contain drivers for SATA controllers, so when you booted from the XP CD, it failed to see the SATA drive.

But, I would think that, if the machine came with XP preinstalled, and it already had a SATA drive, that the drivers would be incorporated into the recovery CD.

Mark: Thanks for your post. My PC crashed and I had to replace the PSU. I am up and running now as of yesterday. This recovery CD of XP is a OEM version of XP Pro (Sp2). I does not recognize my HD because it is a SATA HD. It calls for a floppy which I do not have in the middle of the recovery process. Therefore the restoration is a failure. Tis is the best way I can explain the problem. I hope you or someone else can help me w/ this problem.

---

### Post by Mark Phelps on 2009-08-25
OK, what you will need is a CD containing the SATA controller drivers.  If you have SATA on your motherboard, those drivers would come from the motherboard manufacturer.  In that case, you would find out the make and model of your motherboard and go to their site, where you would use that information to locate drivers, and download the drivers needed for your board.  You would then copy those drivers to a CD (or a diskette if they are small enough to fit on a diskette and you have a diskette reader in your machine).  You could also copy those drivers to a USB stick and insert that when prompted for drivers.

If you have a plugin card that has the controller chip on it, it's the same process but you have to go to the card manufacturer's website to download the drivers.

---

