---
title: "Grub geom Error (file system corrupt?)"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by yo1dog on 2009-06-26
**Basic Problem:**
When installing ubuntu I told it to put the bootloader on my Vista HDD. After, nothing could detect the contents of the HDD and of course, could not boot.

[B]Solution:
[/B]Tried many things with the Super Grub disk, don't know if they helped at all.
Popped in a XP CD (probably could have used Vista CD) and went into repair mode.
Ran fixmbr and fixboot.
Restarted but got an error saying that windows was missing a file.
Popped in a Vista CD and went to repair mode and ran the startup repair.
The startup repair detected a corrupt boot sector and fixed it.
Restarted, voila! Sucess!
Jumped out of seat at site of the Vista logo and began dancing and siging "Can't Touch This" by McHammer.

**Original Post/Situation and full problem:**
Here's the situation: I have vista installed on a sata hdd (we will call this hdd A), I installed Ubuntu on another sata hdd that I took out and put into another computer. When I tried to boot I got some error (I think it was 17, I don’t remember). So I plugged another sata hdd (hdd B) into my comp and installed Ubuntu on that to fix the grub system. That worked however I didn’t want to have to have hdd B plugged in so I installed Ubuntu on hdd B again but told it to put the boot loader on hdd A. Now when I try to boot of off A I get the error: "GRUB geom error". I can boot off of B but I cannot see A in the file browser and the install disk does not detect an OS on A. Also windows vista install disk doesn't detect an OS either.

Here's the question: What do I do: P? I don’t think my hard drive is corrupted and I don’t think that my filesystem is corrupted because the Ubuntu install still detected it as NFTS (or whatever it is).

Here's what I've tried: I looked through my bios and both drives are set to auto mode. I tried installing Ubuntu again on hdd B and putting the boot loader on B.

Thanks for your time and help!
 - Mike

---

### Post by elp4nda on 2009-06-26
> Here's the situation: I have vista installed on a sata hdd (we will call this hdd A), I installed Ubuntu on another sata hdd that I took out and put into another computer. When I tried to boot I got some error (I think it was 17, I don’t remember). So I plugged another sata hdd (hdd B) into my comp and installed Ubuntu on that to fix the grub system. That worked however I didn’t want to have to have hdd B plugged in so I installed Ubuntu on hdd B again but told it to put the boot loader on hdd A. Now when I try to boot of off A I get the error: "GRUB geom error". I can boot off of B but I cannot see A in the file browser and the install disk does not detect an OS on A. Also windows vista install disk doesn't detect an OS either.
:confused:
Hi, sorry I didn't get all that you wrote but from that i got, this should help:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
:D

---

### Post by ajgreeny on 2009-06-26
You made life very complicated by installing on one machine and then moving the disk to another.  Grub will have found the OSs at install time and written the /boot/grub/menu.lst file accordingly.  You have then upset all that the installer did by removing the grub/menu.lst file from the original machine.  Try supergrub and it may help, but don't expect Vista to see your ubuntu install;  it will not be possible without a third-party utility installed in windows first.

---

### Post by yo1dog on 2009-06-26
Thanks for the quick replies.

I will try that Super Grub Disk, thanks.

---

### Post by yo1dog on 2009-06-27
Still no luck. I don't see how that grub disk is supposed to help me.

If someone could tell me how installing the bootloader on my Windows HDD caused these errors I would be very thankful.

The first step I need to take is getting it so I can see the contents of my Windows HDD again. Any ideas?

---

### Post by ajgreeny on 2009-06-27
Boot the ubuntu live CD and mount the ubuntu install and also the windows install disks by double clicking on their icons in places menu.  Now lets have a look at the /boot/grub/menu.lst file from that install.  Just copy the list at the bottom, not all the commented out text above, and start with the first of the ubuntu stanzas.  It will look something like
```
title        Ubuntu 9.04, kernel 2.6.28-13-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=7a49a256-2471-45cc-9933-78b8a5bbcfe9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=7a49a256-2471-45cc-9933-78b8a5bbcfe9 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7a49a256-2471-45cc-9933-78b8a5bbcfe9 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7a49a256-2471-45cc-9933-78b8a5bbcfe9 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```though you may not have the windows paragraph in yours.  Now in the live CD terminal run ```
sudo fdisk -l
``` and copy the output here.  This may allow us to tell you how to install grub to the boot disk and then what menu.lst edits you may need to do to get it to work.

---

### Post by yo1dog on 2009-06-27
That's one of the problems. It does not show up under places. Nothing seems to be able to detect the content of the hdd.

I just tried using repair mode from an XP cd and ran fixboot and fixmbr. When fixboot ran it said something about repairing a corrupt bootsector.

I rebooted and tried to boot off of the HDD but it said that it is missing some system file in <windows>/system32/somefile.exe

Trying the vista cd's repair feature now.

[b]Edit[b]
Progress! Vista cd now detects an OS!

---

### Post by yo1dog on 2009-06-27
[SIZE=6]**SOLVED!**[/SIZE]

Excuse the over sized font but even with all its size, capitalization, and exclamation mark it still under exaggerates my excitement.

Check my first post for how I did this.

---

