---
title: "Dual boot: XP pro will not boot"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by bovineblitzkrieg on 2009-05-04
Hey, if you can help me I'll love you forever.

I had XP on my laptop and it had a recovery partition.  I decided to replace the recovery partition with Ubuntu 9.04.  Somehow, Grub will not boot windows.  It hangs at "Starting up..." and will not proceed any further.  I'm fairly new to Linux, and have read a thousand different guides and forum topics on the issue, but I think the only way I can get this to work is if someone can help me out directly.  Some info:

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c4ca370

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       18098   145364152+   f  W95 Ext'd (LBA)
/dev/sda2           18099       19192     8787555   83  Linux
/dev/sda3   *       19193       19457     2128612+  82  Linux swap / Solaris
/dev/sda5               2       18098   145364121    7  HPFS/NTFS

-----------------------------------------

sudo gedit /root/grub/menu.lst

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        bffb3c96-90b0-4fe9-b8bd-88ea7361d0a5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bffb3c96-90b0-4fe9-b8bd-88ea7361d0a5 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        bffb3c96-90b0-4fe9-b8bd-88ea7361d0a5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=bffb3c96-90b0-4fe9-b8bd-88ea7361d0a5 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        bffb3c96-90b0-4fe9-b8bd-88ea7361d0a5
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP
rootnoverify    (hd0,0)
savedefault
chainloader    +1

------------------------------

Thanks in advance.

---

### Post by bovineblitzkrieg on 2009-05-04
If I put "makeactive" in the grub menu, it says "Invalid device requested"

---

### Post by LoloftheRings on 2009-05-04
What about 
```

title        Windows XP
root        (hd0,0)
makeactive
chainloader    +1

```

This is the example taken from the menu.lst generated file.

I hope this might help you..

---

### Post by bovineblitzkrieg on 2009-05-04
I just get "invalid device requested"

I have no idea why it won't boot, or why the partition says w95

---

### Post by caljohnsmith on 2009-05-05
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

