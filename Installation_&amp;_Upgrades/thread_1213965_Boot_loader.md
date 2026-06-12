---
title: "Boot loader"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by elmnas on 2009-07-15
Hi I have ubuntu 9,04 and windows 7 (Dual boot loader) of a mistake I removed the whole windows 7 string thing from /menu.lst so when I restart computer I cant see the windows 7 I checked I installed the grub boot loader on (hd1,1) how can I get it back.? please help me.

---

### Post by carml on 2009-07-15
Boot in Linux,then go to Applications->Accessories->Terminal and type
```
gksu gedit /boot/grub/menu.lst
```
You'll be prompted to insert your password.
Add the name of the OS (in your case Win7) as in my menu.lstshown below,then save the file and reboot.
At reboot you should be able to boot into Win7
```
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=05f76567-3619-4134-9a29-dffff19d405d ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=05f76567-3619-4134-9a29-dffff19d405d ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```
That should work to have Win7 bootable,if you need more help just ask. :)

---

### Post by Mark Phelps on 2009-07-15
Depends on what you're seeing when you boot...

If you see a GRUB menu but there's no entry for Windows 7, that's one fix.

If you're not seeing a GRUB menu and are going straight into Ubuntu, that's a different fix.

Also, the details of the fix depend on how many physical drives you have in your machine and whether or not you're booting from the drive containing Ubuntu.

Please reply to the questions above and post the result of "sudo fdisk -lu" in a terminal (that's a lower case L, not a one).

---

