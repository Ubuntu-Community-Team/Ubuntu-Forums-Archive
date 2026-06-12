---
title: "Can't startup Windows anymore"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by Magnificence on 2009-06-11
I installed Ubuntu a while ago through wubi.exe in Windows XP to try it. So I liked it and installed it normally with a Ubuntu CD. Now the 'normal' Ubuntu works wonderful.
I use GRUB as boot menu. But in the boot menu I can start "Windows NT/2000/XP (loader)" and another "Ubuntu" wich starts the 'wubi' Ubuntu. But the "Windows NT/2000/XP (loader)" doesn't start my Windows XP, instead there comes a message saying something like: "Packard Bell recovery program" wich has a load bar. After that there is nothing. A black screen with only a flashing "_".
I have to notice that I installed Windows XP from a setup that comes from a hidden partition. The computer comes from Packard Bell so the setup of Windows XP texted with "Packard Bell" all over the place.

So can someone please help me? I want to do some things on WIndows again :).

EDIT: When I choose "Ubuntu" in GRUB, that's the wubi Ubuntu, I CAN choose "Windows XP Home Edition", but if I choose that, it goes to the wubi Ubuntu boot menu again.

---

### Post by dstew on 2009-06-11
It sounds like your grub menu is mis-configured. When Ubuntu is installed, there is a program that tries to create a proper grub menu, but sometimes it comes out wrong. Often it is the recovery partition that causes issues.

To fix it, you need to edit the grub menu file. To figure out exactly how to edit the file, we need to know what the disk partitions are. Boot the "normal" Ubuntu, and on a command line (System --> Accessories --> Terminal) enter the commands```
sudo fdisk -l
cat /boot/grub/menu.lst
```Post the results to the forum.

---

### Post by Magnificence on 2009-06-11
Partitions:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17df17de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1020        4934    31447237+   7  HPFS/NTFS
/dev/sda3            4935       17988   104856255    7  HPFS/NTFS
/dev/sda4           17989       24321    50869822+   5  Extended
/dev/sda5           17989       18249     2096451   82  Linux swap / Solaris
/dev/sda6           18250       24321    48773308+  83  Linux

Disk /dev/sdb: 8054 MB, 8054636032 bytes
255 heads, 63 sectors/track, 979 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d691f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         849     6819561    b  W95 FAT32
/dev/sdb2   *         850         979     1044225    b  W95 FAT32
```menu.lst without most of the comments:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        2c5a5eee-442f-4aa7-ad13-e121533440e4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2c5a5eee-442f-4aa7-ad13-e121533440e4 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        2c5a5eee-442f-4aa7-ad13-e121533440e4
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=2c5a5eee-442f-4aa7-ad13-e121533440e4 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        2c5a5eee-442f-4aa7-ad13-e121533440e4
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Ubuntu
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

```

Thank you in advance ^^.

---

### Post by dstew on 2009-06-11
I see why your Windows menu selection starts the recovery partition. The menu item points to (hd0,0), which is partition sda1. I don't know much about Wubi, so I an not sure if my advice will work. The second Ubuntu item points to partition (hd0,1), which is sda2. When you choose the second Ubuntu menu item, does it go straight to Wubi, or do you get a choice between Wubi and Windows? Maybe what you really want is to boot sda3, which in grub notation would be (hd0,2). Let's try that.

To edit the grub menu, from the Ubuntu desktop, press alt-F2 to get a command line. Then enter```
gksudo gedit /boot/grub/menu.lst
```Find this section:```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```Change the rootnoverify argument to (hd0,2):```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1.
```Save the file and boot again.

---

### Post by Magnificence on 2009-06-11
I tried that already because I already did some search on the forum. But that doesn't work. 

First I get GRUB's boot menu were the last item is 'Ubuntu', wich is the 'wubi' Ubuntu. If I choose that item, it goes to the boot menu of 'wubi' Ubuntu. Let's call wubi Ubuntu's boot menu: "Menu2" and the first boot menu from 'normal' Ubuntu: "Menu1".

First I get Menu1:
 -Ubuntu 9.04, kernel 2.6.28-11-generic
- Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
- Ubuntu 9.04, memtest86+
- Windows NT/2000/XP (loader)
- Ubuntu
So I choose the last item: "Ubuntu", wich directs me to Menu2:
[I don't exacly know anymore wich other items were there to, but those were there defently:]
- Windows XP Home Edition
- Ubuntu
So i choose: "Windows XP Home Edition", wich directs me to Menu2...
If I choose "Ubuntu", I get the Ubuntu wich I installed with wubi.

I only want to be able to startup my Windows again, I prefer to have my Windows in GRUB's boot menu, but I don't mind if there is now other way then around. ^^

---

### Post by dstew on 2009-06-11
Menu 2 is probably the Windows multi-boot menu. I don't know much about Windows multi-boot. I would guess that you will need to re-configure the Windows multi-boot menu somehow. Maybe you can access the Windows boot.ini file through the Ubuntu system, and edit it. See this [Microsoft support page]("http://support.microsoft.com/kb/314081").

---

### Post by Magnificence on 2009-06-11
Menu2 is exacly the same as the GRUB's Menu1, so I gues it is also GRUB. I know how the Windows boot selector looks like, and it is defently not that.

---

### Post by Magnificence on 2009-06-11
only not the same in items :P

---

### Post by dstew on 2009-06-11
At the second menu, instead of choosing an item press 'e' for edit. Look at the Windows item. Post to the forum the lines in that item.

EDIT: Thinking about it, maybe you have a grub boot loader installed in the boot sector of the Windows drive, where normally the Windows boot sector code should be. If so, you can put the Windows boot sector code back in by using the fixboot command from a Windows recovery console.

---

### Post by Magnificence on 2009-06-12
Here is Menu2:
The're 2 items that have 'Windows' in their name.
- Windows NT/2000/XP (loader), wich goes to hd0,0
- Windows XP Home Edition, wich goes to hd0,1

So I think that on sda2/hd0,1 the wrong boot loaders is installed or something.

---

### Post by Magnificence on 2009-06-12
/dev/sda1 is my hidden partition that has therecovery program, i now unerstand why it doesnt startup windows. But it also seems that the recovery program is broke. I think it caused by installing GRUB.

---

### Post by dstew on 2009-06-12
No, it is not the recovery partition that is the problem. Does the first menu item in the second menu start the recovery software?

Anyway, the menu item in your second menu that points to (hd0,1) is causing the problem. What has happened is that you have a grub boot loader installed in the *boot sector* of the partition sda2 in Linux notation, which is the same partition as (hd0,1) in grub notation. That is your Windows partition, and it is the one you want to boot. However, it does not have the Windows boot sector code in place -- grub is in there instead, by mistake. So, the menu item for Windows boots the Ubuntu boot loader that is in there by mistake, and around and around you go.

To fix it, you need to put the Windows boot sector code back into the boot sector of the sda2 partition. Then, when you pick the menu item for Windows in your first menu, Windows will boot.

To restore the boot code into the boot sector of partition sda2, the usual thing is to use the [Windows recovery console]("http://support.microsoft.com/kb/307654"), and the **fixboot c:** command (assuming that the recovery software uses c: for the sda2 partition). If you can't get a recovery console, you might be able to somehow copy the boot sector code from another working Windows computer and install it into the boot sector.

---

### Post by Magnificence on 2009-06-12
OK Thanks, I'll in for it. :)

---

### Post by merlinus on 2009-06-12
You might also try supergrub.

---

### Post by Magnificence on 2009-06-12
I found a cd image for the Recovery Console, started it and typed "fixboot C:". After that it didn't start up anything anymore.

I started the Live CD and say that all the partitions are gone. No files left on my computer.

No I'll reinstall Ubuntu and contact Packard Bell or another company to install Windows again. I gues I don't need any help any more :P.

---

