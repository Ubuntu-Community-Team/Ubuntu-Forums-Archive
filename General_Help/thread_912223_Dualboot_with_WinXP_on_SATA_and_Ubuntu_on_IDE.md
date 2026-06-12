---
title: "Dualboot with WinXP on SATA and Ubuntu on IDE"
date: 2008-09-06
forum: General Help
---

### Post by anderssl on 2008-09-06
I have set up Ubuntu and Win Xp to dualboot on my computer, with WinXP on a SATA drive and Ubuntu on an IDE. It was working fine for a short while, but now I had to reinstall Windows due to a virus - and after formatting the SATA drive and reinstalling Windows, my grub doesn`t work. I have booted from the Ubuntu cd and tried fdisk, but only my SATA drive shows up! So I don`t know how I can restore grub to get it working again. Any tips? Help me, please...:mad:

- And yes, I`m a newb, so please speak slowly and clearly...

Results of fdisk and find /boot/grub/stage1:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe680e680

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       30400   141789690    f  W95 Ext'd (LBA)
/dev/sda5           12749       30400   141789658+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> 


---

### Post by fooman on 2008-09-06
this should help:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by anderssl on 2008-09-06
Ok, maybe, but as I said my IDE doesn`t show up with fdisk, do I have to use the Super grub disk?

---

### Post by wolfen69 on 2008-09-06
in the future, when using seperate drives, you could unplug one drive while installing xp, then unplug xp and install ubuntu. then you can choose at startup which one to boot to. much easier than fooling with grub. that way grub will always be on the ubuntu drive.

---

### Post by anderssl on 2008-09-06
Ok, thanks again - but as I said I'm a newb, so: What exactly is it I need to do, now? The Super Grub Disk option, or something else?

---

### Post by caljohnsmith on 2008-09-06
Super Grub Disk is unfortunately not going to help you at this point; the problem is your IDE drive is not even recognized by your computer. Have you checked your IDE HDD's connections? Have you changed any jumper wires or BIOS settings? Once you can get fdisk to show your IDE HDD, it will be easy to fix your problem.

---

### Post by anderssl on 2008-09-10
I`m struggling. I realized that I hadn`t done the Windows installation quite properly, so I decided to do it over - this time disconnecting the IDE disk in the process. Now I have reconnected the IDE, but it`s the same as before. I hadn`t changed any jumper settings (the IDE is slave), or BIOS except for boot priority, which I changed to CD for the install disk. As for HDD connections, I`m not sure what you mean - but basically I haven`t done anything else than installing Win XP on the SATA and followed instructions... But something must have been messed up in the bios, cause the IDE shows up in the boot device list in bios setup with all funny characters instead of its real name (but yes, at least it is in the list).

The strange thing is, if I disconnect the SATA my IDE shows up fine (except if changing the jumper settings to make IDE master, then nothing works, not even bios setup).

I`ll try to reinstall ubuntu now. If that doesn`t help, I`m lost...

---

### Post by anderssl on 2008-09-10
...and now I have officially given up. I have tried messing around with jumper settings on the ide (master/slave), boot device priority in bios and disconnecting the SATA. No results:
1. I can not boot my ubuntu installation (which is on the IDE drive)
2. When booting from ubuntu cd, I can not see the IDE drive
3. ...and so I can not re-install ubuntu, format the IDE drive or do anything with it at all
4. I have reloaded defaults in bios, and I disabled quick boot. After that, the IDE shows up normal in bios, but the problems above persist.
5. I also can not see the IDE drive in windows.

I can't really believe the drive is entirely dead, cause the computer fails in different ways depending on the jumper settings on the drive... but not very useful information. Do anyone have any advice on this, or shall I just throw away my IDE?

I have to tell you guys, I started installing ubuntu some time this spring in order to see if that could give me less problems than windows. Now it's september, and the only result is that I can throw my hard drive out the window. I'm not really impressed. Well ok the one thing I'm impressed with is people's readiness to help, thanks a lot! But no result in the end.

And yes I'm a linux newb, but I'm also studying computer science at university level. Do I really need to finish my PhD before I can use this system?

:(

---

### Post by caljohnsmith on 2008-09-10
> **anderssl said:**
> But something must have been messed up in the bios, cause the IDE shows up in the boot device list in bios setup with all funny characters instead of its real name (but yes, at least it is in the list).

The strange thing is, if I disconnect the SATA my IDE shows up fine (except if changing the jumper settings to make IDE master, then nothing works, not even bios setup).

Based on all your computer's symptoms, I don't think your problem has anything to do with Ubuntu or Windows at this point, so I don't think it is accurate to blame Ubuntu.

Can you put your IDE drive in another computer just to check it? If it works perfectly in another computer, then the problem is most likely your BIOS. You shouldn't be seeing "funny characters" for it of course. If the IDE drive checks out fine in another computer, I would consider re-flashing your BIOS and with the latest version.

---

### Post by anderssl on 2008-09-11
Well, funny that the harddrive should fail just as I started messing with my dualboot though... On the other hand it was getting old, and I was thinking of getting a new one. So no big harm done. Thanks for your help though.

---

