---
title: "Dual boot Ubuntu-Win XP. Now single boot Ubuntu!!"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by danp451 on 2009-06-11
Hi All,

I know this is a common thread and I've traced several with no luck so hoping someone can help.

I have created a dual boot machine of Windows XP (Home) and Ubuntu 9.04. Now when I try to boot into Windows I get an error telling me that Windows cannot boot and I need the installation disk. I can no longer even access the Recovery partition.

I can still see the files on the Windows partition and all of the boot files that are on there.

I don't mind too much if I have to lose Windows completely but would be very satisfied if I can (with your help) solve this and keep a small Windows partition on here for the bare necessities.

As a starter here's the output of sudo fdisk -l followed by the non-commented bits of menu.lst - Am a bit disturbed by the partition on cylinder boundry bit......

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00028941

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5120000   12  Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         638       12340    93992869    7  HPFS/NTFS
/dev/sda3           12341       19457    57167302+   5  Extended
/dev/sda5           12341       13621    10289601   82  Linux swap / Solaris
/dev/sda6           13622       19457    46877638+  83  Linux

Menu (minus comments)
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        23d1f966-72bd-48e7-9e31-6909b6f68bae
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=23d1f966-72bd-48e7-9e31-6909b6f68bae ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        23d1f966-72bd-48e7-9e31-6909b6f68bae
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=23d1f966-72bd-48e7-9e31-6909b6f68bae ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        23d1f966-72bd-48e7-9e31-6909b6f68bae
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1




Many thanks,

Dan

---

### Post by Darkaiser on 2009-06-11
check this out bro
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by danp451 on 2009-06-11
THanks. I have seen this one already. Will have another look through to see if I missed anything.

D.

---

### Post by presence1960 on 2009-06-11
> I have created a dual boot machine of Windows XP (Home) and Ubuntu 9.04. Now when I try to boot into Windows I get an error telling me that Windows cannot boot and I need the installation disk. I can no longer even access the Recovery partition.

you probably need to fix windows bootloader : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) after doing this check to see if your machine boots directly into windows. If it does then you will need to boot off the Ubuntu Live CD to restore GRUB; Boot the CD and choose "try Ubuntu without any changes." Follow this guide to restore GRUB:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

#4 should say (hd0,5)
#5 type root (hd0,5)
#6 type setup (hd0) to place GRUB in the MBR

After rebooting without the Live CD :

To access your recovery partition add this to menu.lst after the windows entry by running in terminal > gksu gedit /boot/grub/menu.lst

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows Recovery
rootnoverify	(hd0,0)
chainloader	+1
```

---

### Post by danp451 on 2009-06-11
Thanks.

Only problem is that this is an Advent netbook with no CD drive. You've given me some more threads to pursue though!

Can boot off USB fine.

Any experience of Super Grub?

D.

---

### Post by presence1960 on 2009-06-11
> **danp451 said:**
> Thanks.

Only problem is that this is an Advent netbook with no CD drive. You've given me some more threads to pursue though!

Can boot off USB fine.

Any experience of Super Grub?

D.

Well having a netbook definitely puts a damper on things since you have no CD drive. If you create a bootable usb for Ubuntu you will be able to edit the menu.lst file to add the recovery partition entry. As a last resort you can recover from there, but then you will have a lot of work to do after the recovery. I would try a USB Cd drive and try to borrow a windows install disc to run fixmbr in recovery console, then boot off the Ubuntu USB or CD and restore GRUB before I use the factory recovery partition.

No experience with Super Grub Disk, have never had to use it, always have been able to solve my GRUB problems without it. But I am sure others can help you with that.

---

### Post by danp451 on 2009-06-12
Thanks. I am going to pursue this method now as a friend has the same as me so will create a recovery disc from her and boot into RC via USB - am sceptical about this and am sure will end up having to find USB CD drive and installation disc.

Will post back with outcome in case it helps others.

D.

---

### Post by raisinglinux on 2009-06-12
I didn't read the post in full but can't the UBCD on USB key provide a quick solution?
 
[http://raisinglinux.com/2009/utilities/ultimate-boot-cd-free-computer-repair-toolkit/](http://raisinglinux.com/2009/utilities/ultimate-boot-cd-free-computer-repair-toolkit/)

---

