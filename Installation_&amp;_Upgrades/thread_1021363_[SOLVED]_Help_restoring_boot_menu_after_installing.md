---
title: "[SOLVED] Help restoring boot menu after installing xp"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by haran_hockey on 2008-12-25
I originally had 2 paritions, xp on the C:\ drive(my main partition) and nothing on the other partition(E:\) But my xp got screwed up so I installed Ubuntu 8.10 on the E:\ partition. Everything is working fine and I decided to totally reinstall xp on the C:\ partition. After the xp install, the option for Ubuntu doesn't show up on startup so I followed this link: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

But when I put in, setup (hd0) , it said it couldn't mount it or something. I'm assuming this is because my main partition or 'hd0' is my xp partition. So I just want to fix it so I can dual both and see the screen so I can choose xp or ubuntu.

---

### Post by namdung on 2008-12-25
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by taurus on 2008-12-25
Maybe this helps, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

---

### Post by albinootje on 2008-12-25
> **haran_hockey said:**
> I originally had 2 paritions, xp on the C:\ drive(my main partition) and nothing on the other partition(E:\) But my xp got screwed up so I installed Ubuntu 8.10 on the E:\ partition. Everything is working fine and I decided to totally reinstall xp on the C:\ partition. After the xp install, the option for Ubuntu doesn't show up on startup so I followed this link: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

But when I put in, setup (hd0) , it said it couldn't mount it or something. I'm assuming this is because my main partition or 'hd0' is my xp partition. So I just want to fix it so I can dual both and see the screen so I can choose xp or ubuntu.

Here are good instructions :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by haran_hockey on 2008-12-25
Thanks a lot everyone(you all gave same site) but I was wondering if you can help me with 1 small thing and that is changing the name to Windows xp instead of Windows longhorn or something.

---

### Post by albinootje on 2008-12-25
> **haran_hockey said:**
> Thanks a lot everyone(you all gave same site) but I was wondering if you can help me with 1 small thing and that is changing the name to Windows xp instead of Windows longhorn or something.

In Ubuntu do the following in a terminal :
```

sudo gedit /boot/grub/menu.lst

```
Go all the way down in that file, change the name.
Exit and save gedit (the text editor).
Reboot to test it.

---

### Post by nathockens on 2008-12-25
Hey everyone,
I'm having a similar problem after installing Ubuntu from the Desktop CD inside of XP.

The problem is with the windows Boot Record. Right now it reads:

> 
[boot loader]
timeout=10
[operating systems]
c:\wubildr.mbr="Ubuntu"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect


I tried putting "c:\wubildr.mbr="Ubuntu" above the other operating system and also put it as:
default=c:\wubildr.mbr="Ubuntu"

But putting it above doesn't matter (default still goes to XP) and changing the default as written just creates an error.

I also went through the above guide but on typing "find /grub/stage1" or "find /boot/grub/stage1" I stll get Error 15.

Running fdisk -l only shows an NTFS partition.

Any ideas? I'm really irritated.

---

### Post by nathockens on 2008-12-25
Here are the contents of my wubildr.mbr file on the c: root:
> 
scrambled crap
---
Press space bar 
Press   to start GRUB, any other key to boot previous MBR ... 
Timeout :      
Invalid previous MBR. Press any key to start GRUB ... 
Cannot find GRLDR.  to hold the screen, any other key to boot previous MBR ... 
Error while reading MBR of  drive (hd0 )  
Invalid boot indicator in partition table of  
Invalid sectors_per_track in partition table of  
Invalid start_sector in partition table of  
Invalid end_sector in partition table of  
No boot signature in partition table of  
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart. 
Try (hd0,0 ) :  EXT2:  NTFS4:  NTFS5:  NTFS5p:  FAT32:  FAT16:  FAT12:  non-MS: skip  Extended:  invalid or null  This partition is NTFS but with unknown boot record. Please
install Microsoft NTFS boot sectors to this partition correctly, or create an
FAT12/16/32 partition and place the same copy of GRLDR and MENU.LST there.                             hot-key        GRUª


Also, under System Properties | Startup and Recovery the default OS is set to "Ubuntu"

---

### Post by albinootje on 2008-12-25
> **nathockens said:**
> Here are the contents of my wubildr.mbr file on the c: root:


Also, under System Properties | Startup and Recovery the default OS is set to "Ubuntu"

Your question is Wubi specific (I have no experience with Wubi). 
I think it makes sense to start a new thread for your question in the Wubi related support section.
Just my 2 cents.

---

### Post by nathockens on 2008-12-25
Wubi? What's that?

---

### Post by albinootje on 2008-12-25
> **nathockens said:**
> Wubi? What's that?
What is Wubi :
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Here's the ubuntuforums Wubi FAQ :
[http://ubuntuforums.org/showthread.php?t=396526](http://ubuntuforums.org/showthread.php?t=396526)
Here's the Wubi sections :
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

