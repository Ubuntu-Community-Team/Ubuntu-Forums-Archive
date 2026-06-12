---
title: "Help! Grub Error 17"
date: 2008-11-24
forum: General Help
---

### Post by ndruu on 2008-11-24
Hi. I am really concerned, and unable to boot into either my Windows Vista or Ubuntu 8.10. I was online with firefox in Ubuntu when firefox disappeared (although pandora kept playing) and the borders on pidgin disappeared also. I figured some process had crashed. I tried to shutdown my machine by clicking the power icon and selecting shutdown. That worked, but when I turned it back on I am presented with grub error 17 before I am able to select windows or ubuntu. 

This is really unfortunate because I really need to be able to use the software on my windows partition for work.

I've read around on the forums and understand that posting the output of sudo fdisk -lu is helpful, so here it is...



[SIZE="1"]andrew@andrew-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcb81a0ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   283258079   141629008+   7  HPFS/NTFS
/dev/sda2       283258080   312576704    14659312+   5  Extended
/dev/sda5       283258143   311243309    13992583+  83  Linux
/dev/sda6       311243373   312576704      666666   82  Linux swap / Solaris

Disk /dev/sdb: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00051ffd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    14876189     7438063+  83  Linux
/dev/sdb2        14876190    15631244      377527+   5  Extended
/dev/sdb5        14876253    15631244      377496   82  Linux swap / Solaris[/SIZE][/SIZE]



Someone please help me repair this so that (preferably) both operating systems are usable without having to reinstall either one. I can't reinstall windows myself anyways, as its a company owned machine that I don't have the software for. 

Thanks,

Andrew

---

### Post by polymath on 2008-11-24
For starters, the easiest way to recover windows is to use a grub boot disk and just rootnoverify(part) then chainloader +1

It's pretty easy to create a boot disc/floppy and will let you use the original computer while you try and fix the problem.  The only real downside is having to have the disc inside the computer at startup.

Before I ramble about GRUB that may or may not matter, you might want to check out this thread:  [http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

You may also want to try reinstalling grub with grub-install.

IF THE ABOVE LINK DOESN'T WORK, YOU CAN TRY TO DECIPHER MY RAMBLINGS BELOW:

This is all based on quickly skimming the grub documentation.

The GRUB documentation says that error 17 is caused by:
> 
17 : Cannot mount selected partition. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.


Earlier it says this:
> 
The general way that the Stage 2 handles errors is to abort the operation in question, print an error string, then (if possible) either continue based on the fact that an error occurred or wait for the user to deal with the error.

The following is a comprehensive list of error messages for the Stage 2 (error numbers for the Stage 1.5 are listed before the colon in each description):


And in stage 1.5 errors:
> 
The general way that the Stage 1.5 handles errors is to print an error number in the form Error num and then halt. Pressing <CTRL>-<ALT>-<DEL> will reboot. 
The error numbers correspond to the errors reported by Stage 2. See Stage2 errors.  


Since  It just prints the error number and not the error string, we can assume it is a stage 1.5 error.  To understand this you have to understand that GRUB comes in three stages, 1, 2, and 1.5.  Stage 1 sets up the system, and boots stage 1.5.  Stage 1.5 comes in many types (e2fs_stage1_5, fat_stage1_5, etc), and these set up the partition for stage 2, which is what boots and such.

If stage 1.5 can't mount the partition, it's an error for with the partition-specific 1.5 image, either that it's missing/corrupt or has a bug.

That's all i could deduce in limited time.  This is all pure conjecture, and i'm probably wrong on most of these points, but i did what i could.  I warn you, i'm not a grub expert.

Try the link first.

---

### Post by caljohnsmith on 2008-11-24
Hi Andrew, so it looks like you have linux installed on both your sda and sdb drives; which one is Ubuntu 8.10? Most likely the reason you are getting a Grub error 17 right now is your Intrepid file system needs repairing after your "unclean" shutdown. How about booting your Live CD, open a Terminal (Applications > Accessories > Terminal), and do:
```
sudo fsck -y /dev/sda5
sudo fsck -y /dev/sdb1
```
If fsck successfully completes on those partitions, reboot, and let me know if you still get the Grub error 17; we can work from there if you want. :)

---

### Post by ndruu on 2008-11-24
Caljohnsmith, you are a linux god. Thank you for your assistance. Just in case you were wondering about the sda and sdb thing... My laptop has a 160gb harddrive which is dual booting vista and ubuntu 8.10. 

sda1 is vista, sda5 is ubuntu. When I started getting the error 17, I couldn't really use the forums without getting onto my computer somehow, so I pulled out my ubuntu 8.10 usb stick, and thats the sdb1.

Anyways, I knew it was gonna be something simple like that, but I just don't know enough about the command line to have figured that one out on my own. So thanks again. Everything's working fine now, except all my customized firefox settings, bookmarks, and add-ons are gone. Looks like that part was lost in the crash for some reason.

---

### Post by caljohnsmith on 2008-11-24
That's great news you successfully booted back into Ubuntu. Sorry to hear that all your Firefox add-ons and such are gone. You might want to poke around the following directory:
```
/home/<your username>/.mozilla/firefox
```
And you might find your lost bookmarks/extensions/add-ons, etc. Anyway, good luck. :)

---

