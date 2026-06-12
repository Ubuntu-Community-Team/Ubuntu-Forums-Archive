---
title: "Installation help needed"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by keefeba on 2009-05-29
[FONT=Arial][SIZE=2]I recently attempted to install ubuntu 8.04 from a disk onto laptop (toshiba satellite a205-s5843).    My goal was to partition the HD and keep vista for dual boot configuration.[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]The result is that ubuntu works almost fine (system> admin> Network> does not show the wireless option so I have been unable to configure wireless access).  [/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]Vista will not open in any fashion.  Not safe mode not last known good configuration not any of the many options available from the F8 option list at start-up.   I dislike vista so I decided to attempt to scrap the whole thing, boot from the cd drive to install XP, reformat everything, and start over.  No such luck.  Windows tells me…  “Setup did not find any hard disk drives installed on your computer.  Make sure any hard disk drives are powered on and properly connected to your computer and that any disk-related hardware configuration is correct.  This may involve running a manufacturer-supplied diagnostic or setup program.  Set up cannot continue.”[/SIZE][/FONT]
[FONT=Arial][SIZE=2] [/SIZE][/FONT]
[FONT=Arial][SIZE=2]So it appears the partitioning failed in some fashion.  I am happy to fix that or start over and reformat entire drive.  I have no experience on ubunto except what I explained here.  Suggestions for quickest path to some version of dual boot configuration?  Thanks.[/SIZE][/FONT]

---

### Post by 73ckn797 on 2009-05-29
If you have the Ubuntu LiveCD boot from it and run Ubuntu by selecting the first option. Once in go to System/Administration/Partition Editor. What does it show about the hard drive (HDD)?

---

### Post by pastalavista on 2009-05-29
Your drive was still formatted to ext3 for Ubuntu and Windows can't do anything with it so it has no space to install in. Boot from the Ubuntu live CD and run System > Administration > Partition Editor. Just delete the whole partiton and the Windows install disk should work OK. You could also just resize/shrink the Ubuntu partition and format the recovered space to NTFS or FAT32. Windows will install in the free space and leave Ubuntu intact, except for the boot loader (grub). To dual boot, you'd just need to reinstall grub (with the Ubuntu CD) after you install Windows.

---

### Post by keefeba on 2009-06-01
thanks for the help.  I booted from ubunto cd and delted the partion.  No Change.  XP disk still says the same "setup did not find any hard disk drives installed..." mentioned below.

---

### Post by lindsay7 on 2009-06-01
I would try using the ubuntu live cd to boot up, right click the partiton one at a time if there are any and unmount the partition and delete it and leave the space unallocated. Do this until the whole drive is unallocated. Then install one partition for the whole drive and format it fat 32 for now.

Then see if you can install windows. If you can, and shrink the partition if you want and install ubuntu or use the ubuntu install process to set it up and partition it.

---

### Post by keefeba on 2009-06-01
[COLOR=black][FONT=Verdana][FONT=Arial][SIZE=3]thanks.  I'm still stuck, though.   I can't seem to delete or unmount the dev/sda2 which is in the "extended" filesystem.  I can delete the other, leave it unallocated or format to fat 32. but neither allows me to get any different result when I try and get XP to install.  the dev/sda2 has the little keys icon next to it so I imagine its locked and that&#8217;s why I can't unmount it.  Manage flags and information are the only non greyed-out options.[/SIZE][/FONT]
[/FONT][/COLOR]

---

### Post by keefeba on 2009-06-01
hold on - I got rid of the keys by clicking the swap icon which appears if I right click the graphic of the partition.  I am now reformating the whole thing as one partition to fat 32.  this will take a while.  I let you know what happens - thanks.

---

### Post by lindsay7 on 2009-06-01
Yes that is the way you unmount the drive. You can not work on it if it is mounted.

---

### Post by keefeba on 2009-06-01
[FONT=Arial][SIZE=3]ok. I had one partition of 149G formatted to fat32 and rebooted from the XP install disk.  I still get the same original error msg: set up did not find and hard disks installed on your computer. ...  what am I missing?[/SIZE][/FONT]

---

### Post by lindsay7 on 2009-06-01
Is this a SATA drive. If so is you bios set for sata drives?

---

### Post by lindsay7 on 2009-06-01
If it is a sata drive and changing the bios does not help, take a look at this...


[http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/)


[http://www.windowsreinstall.com/winxppro/nohdd/indexfullpage.htm](http://www.windowsreinstall.com/winxppro/nohdd/indexfullpage.htm)

---

### Post by pastalavista on 2009-06-01
OK, now I believe I know your problem. I think your 'install' disk is really just a 'restore' disk and it needs to use a hidden restore partition that was on the drive when you originally bought it but got erased when you installed Ubuntu. Probably the only way you'll be able to re-install Windows is to borrow an install disk from somebody and use the "windows key" number that should be on a sticker on the bottom of the laptop or possibly in the paperwork you got with the machine.

---

### Post by keefeba on 2009-06-02
Thanks for the help. 
 
To Lindsay, its SATA.  I don't know how to determine if the bios is set for that or not.
 
To  Pastalavista.  I'm pretty confident my xp disk is the actual software.  It has a product code on the back and I used after a reformat of another laptop and used it to install xp home.

---

### Post by keefeba on 2009-06-02
To Pastalavista. I'm pretty confident my xp disk is the actual software. It has a product code on the back and I used after a reformat of another laptop and used it to install xp home.

---

### Post by keefeba on 2009-06-02
oh - thanks

---

### Post by lindsay7 on 2009-06-02
You normally type f2 or the delete key at start up to get into the bios. You should get a message  at start up telling you this. When you get in look at the menus and see if you find one that talks about sata and ide drives. Make sure it is set for sata.

---

### Post by gnoob on 2009-06-17
hey this is Alden.
Any luck getting into the bios? I imagine that it is already configured to use sata because you were already using the same SATA drive with vista.
I have been doing a little reading and what i have learned is that windows xp does not initially know how to see/use SATA drives.  (SATA is a newer, faster hard drive standard, the older one is IDE)
To use a SATA drive xp needs other drivers, which can be added. (Lindsay's howtogeek tutorial looks the clearest.)  But the process of adding them has many steps and it would be nice to avoid doing that.
One easy way to avoid this would be to install a newer version of windows which supports SATA natively (vista or win7). Have you tried installing vista?  If you dont have a vista disk you could install windows 7.  A pre release version of windows 7 is free and i hear it is very polished and not buggy.  I could make you an install disk for windows 7 if you dont want to bother (but its not too difficult).

---

### Post by St.Aimath on 2009-06-18
Umm, I have a similar mess.
Resolved by deleting all partions using XP install, then creating new ntfs partion, say half the drive, to install M$ on that.
Then boot from Hardy, use the partioner there to make ext3 and swap space in the rest of the available drive.
To get more fancy another partition space could be made to share docs, pics etc.
Is a learning process, try, muck up, do again, muck up, retry, sigh

---

