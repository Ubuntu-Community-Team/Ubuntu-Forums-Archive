---
title: "USB Kubuntu now giving grub 1.5 error 17 ?"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-02-23
This week I installed Kubuntu 8.10 directly on my 8gb usb key. At the office (can't boot at home because of PC USB booting hardware bug) I used to be able to boot off that USB key directly. Now tonight, I wind up with a GRUB 1.5 error 17

I did a bit of googling but still don't understand what is wrong.

 I attached 2 files : 
- boot_info_script result
- misc infos about my folders, fstab, device map, ...

The bios of this office PC is currently set as :
1st boot = cd 
2nd boot = my usb key
3rd boot = floppy
4th boot = hd

Its 23:50 and I am here up to 7am and writing this with Konqueror right off the LIVE CD (have no other Linux access). My USB key is plugged in.

---

### Post by Browser_ice on 2009-02-24
Looking at the boot_info_script result, I see something weird:
> => Windows is installed in the MBR of /dev/sda
 => [B]Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.[/B]

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

**sdb1:** _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb1 and 
                       looks at sector 7471167 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. [B]Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.[/B]
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

It looks like the USB MBR is looking on the wrong partition.

[added comments]
I did the followings which seam to have fixed it. 
root (hd0,1)
setup (hd0)

I booted up in the Kubuntu that is installed on my USB. Again this is not a LIVE CD version but a full regular installation done on the USB key just like you would do on a normal HD. I had formated my USB key as : partition-1=ext2 6.5Gb, partition-2=swap 1Gb.

I will need to test the persistency of my USB Kubuntu and also make sure I did not mess up the office PC Windows MBR. If both of these work, I will report back here and what's left to do now is figure out how to boot with it at home.

Testing ...

---

