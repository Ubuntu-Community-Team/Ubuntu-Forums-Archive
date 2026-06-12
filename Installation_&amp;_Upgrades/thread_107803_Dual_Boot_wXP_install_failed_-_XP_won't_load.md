---
title: "Dual Boot w/XP install failed - XP won't load"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by datamstr on 2005-12-24
After installing Ubuntu 5.10 on my XP Machine, loading windows now fails. During Ubuntu installation, Win XP was found during the Ubuntu installation and a message was displayed "Installing GRUB in the MBR should be OK". Well, after reboot, when I select Win XP, I get a message "File System not found" or something like that. Question: Is it possible to restore the MBR for Win XP or do I have to start from scratch? Any ideas on how to recover?
TIA,
David

---

### Post by fordfan753 on 2005-12-24
what partition is XP on?

Try with grub command line:

```
rootnoverify (hd0,0)
chainloader +1
boot
```

---

### Post by datamstr on 2005-12-24
OK, following is some more information:

_Results of fdisk:_

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hda2            2433        9568    57319920   83  Linux
/dev/hda3            9569        9733     1325362+   5  Extended
/dev/hda5            9569        9733     1325331   82  Linux swap / Solaris

_Results of GRUB commands:_

grub> rootnoverify (hd0,0)

grub> chainloader +1

Error 21: Selected disk does not exist

grub>

_Messages during attempted boot of XP:_

Booting 'Microsoft Windows XP Home Edition'
 
root  (hd0,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1
 
[COLOR="Blue"]note: system hangs at this point[/COLOR]

Why is the boot loader not seeing the NTFS?

Thanks,
David

---

### Post by fakie_flip on 2005-12-25
I had the same problem you mentioned in your first post. The only way I have ever been able to successfully dual boot xp professional with ubuntu 5.10 is by using a seperate harddrive for windows and one for Linux. I will start with a new copy of windows on my computer and leave free space for Linux. After this copy of xp has been installed, it works. Then I begin the ubuntu 5.10 installation. I use the option "use the largest continous free space". Later after the computer has rebooted and the 5.10 cd is out of the computer, grub finds xp asks me to install to the mbr. I click "YES". After this Ubuntu works great without needing sound drivers, but Windows won't load. Windows says that some file is missing when I chose it from the grub menu. The problems with windows never happen untill after the linux install, so I know that it cannot be a bad copy of windows. I really want to know how to fix this problem. Thanks.

---

### Post by Sef on 2005-12-25
Since XP needs on hda1, is it marked as bootable?

---

### Post by Ashtonian on 2005-12-26
Agggg! I'm having the same problem! I followed every single one of [these]("http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/windowsxp.html") directions, but I can't boot into Windows. I get as far as completing and then Windows booting fail. HELP!

---

### Post by Sef on 2005-12-26
Get a Windows boot floppy disk, insert it, restart your computer, and then fdisk/mbr.   Restart it and that should work.

---

### Post by kaamos on 2005-12-26
Doesn't that mess up grub?

---

### Post by datamstr on 2005-12-27
Hello Members,

I tried the dual boot install on another XP machine. When you get to the GRUB install part, just choose the first Ubuntu Partition instead of the MBR. That machine works fine for me using dual boot.

---

