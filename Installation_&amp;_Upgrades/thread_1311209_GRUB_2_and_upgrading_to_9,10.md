---
title: "GRUB 2 and upgrading to 9,10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Howard Kaikow on 2009-11-02
[https://help.ubuntu.com/community/KarmicUpgrades]("https://help.ubuntu.com/community/KarmicUpgrades") states:

> Unable to Load Linux Drive

One of the popular problem that some people faces when they upgraded to Karmic Koala is that Karmic is unable to load their Linux Drive. Ubuntu will prompt an error message:

Gave up waiting for root device. Common Problems:

- boot args (cat /proc/cmdline)

- Check root delays (Did the system wait long enough ?)

- Check root : (did the system wait for the right device?)

- missing modules ( cat /proc/module; /ls/dev)

- Alert /dev/disk/by-uuid=[XXX] does not exist. Dropping to a shell.

A work around for this problem is to tell Grub to load our Linux drive using the absolute drive path and not its UUID. In order to so this, we need to determine whether our Ubuntu is using the legacy Grub or Grub 2. Check your /boot/grub. If this folder contains grub.cfg this means we are running Grub 2. If not then you will are running a legacy Grub.

Legacy Grub

If you are still running the legacy grub then you need to edit your /boot/grub/menu.lst file. Replace the UUID for your Linux drive to the absolute path of your Linux drive. In the following example we tell Grub to find our Linux drive using its full path instead of this UUID /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3

title       Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,2)
kernel      /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3
initrd      /boot/initrd.img-2.6.31-14-generic
quiet

Reboot your Ubuntu after you save menu.lst.

Grub 2

Open /etc/default/Grub. Uncomment the following line:

GRUB_DISABLE_LINUX_UUID=true

Run update-grub in your command line to update your Grub configuration. Now reboot your system. 

I have the folowing in menu.lst.

> title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7ddf536f-6ad6-4063-ab78-e0af592e6988
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7ddf536f-6ad6-4063-ab78-e0af592e6988 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7ddf536f-6ad6-4063-ab78-e0af592e6988
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7ddf536f-6ad6-4063-ab78-e0af592e6988 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7ddf536f-6ad6-4063-ab78-e0af592e6988
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Windows NT/2000/XP (loader)
rootnoverify	(hd0,0)
makeactive
chainloader	+1

I used [Windows-Ubuntu Multiboot]("http://www.standards.com/index.html?WindowsUbuntu") to install 9.04 on a multiboot Windows 2000/Ubuntu 9.04 system.

My C:\boot.ini contains

> C:\grubboot.lnx="Ubuntu Linux"

I'd like to prepare menu.lst in advance of attempting to upgrade to 9.10.

In menu.lst, do I need to replace all uuid with root?
In the current menu.list, root is used without an argument.
I'm guessing this is because I had used the following when installing 9.04.

> $ sudo grub
type your password
grub> device (hd0) /dev/sdg
grub> device (hd3) /dev/sdg
grub> root (hd3,5)
grub> setup (hd0,5)
grub> quit
$ sync
$ reboot

If I do need to specify the root, do I use (hd3,5) or (hd0,5)?

And then start GRUB and

GRUB_DISABLE_LINUX_UUID=true

---

