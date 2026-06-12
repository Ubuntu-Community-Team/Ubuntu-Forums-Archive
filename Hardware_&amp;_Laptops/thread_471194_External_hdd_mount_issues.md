---
title: "External hdd mount issues"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by clk99 on 2007-06-11
I recently installed Ubuntu 7.04 and I'm liking it a lot, but getting my external hdd to work with me smoothly has been kind of a hastle.  It's an NTFS filesystem, so I installed ntfs-3g in order to make it writable.  For a while nothing was bothering me, but recently I've noticed that if I turn the external on after the computer is booted up it says it is mounted but it doesn't appear on the desktop or computer:/// in the file browser, and if I try to access it from /media/external it gives me a "permission denied" error.

When this happens, if I unmount it with 'umount' then remount it, I can then access through /media/external, but it still does not show on my desktop or in computer:///.  This isn't a huge problem of course, but it is getting to be a little annoying and it is certainly not normal, so I'm just wondering how I can go about troubleshooting this.

Thanks in advance.

---

### Post by clk99 on 2007-06-12
Today when I booted up it didn't automount so I tried to mount it myself and received:

```
$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
Password:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/external -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/external ntfs-3g defaults,force 0 0
```

The last time I turned it off, though, was after my laptop had completely shut down, so there's no doubt it was unmounted.  Anyways, I used 'force' and now the hdd is mounted, but still nothing on the desktop or in computer:///.

Just as a note, I've already tried reinstalling fuse and ntfs-3g.

---

### Post by clk99 on 2007-06-19
I reinstalled Ubuntu, this time Kubuntu.  Not because of hdd problems, just for fun really.  But I still have problems mounting my external.  If I turn it on after my computer is booted up, I will get the default popup in KDE asking what to do, but it still won't actually mount the drive.  By reading some other forums I came up with:```
sudo mount -t ntfs /dev/sdb1 /media/external -o nls=utf8,umask=0222
```...which works great if it fails to mount, but it ALWAYS fails to mount and manually mounting my hdd every time is just an inconvenience.  Would Ubuntu like my hdd more if it were formatted in FAT32?  I'm looking for any type of fix I can get.  Here's my new fstab since reinstalling:```
proc /proc proc defaults 0 0
# Entry for /dev/sda2 (root) :
UUID=25c479d5-18e2-4e3a-bdc1-6d6a8abc90af / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 (swap) :
UUID=2a9a9b5c-2904-4915-aabd-6e7964a088b8 none swap sw 0 0
# Entry for cd/dvd-rw :
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
# Entry for windows partition :
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_CA.UTF-8 0 0
# Entry for external :
/dev/sdb1 /media/external ntfs-3g defaults,users,sync,locale=en_US.UTF-8 0 0
```

---

### Post by ukripper on 2007-06-19
try mounting with ntfs-config, it is in repository:

```
sudo apt-get install ntfs-config
```

---

### Post by clk99 on 2007-06-20
I already have ntfs-config installed and when I open it I only get the dialog with the two check boxes for enabling write support to internal/external devices.  Making sure they are both checked and hitting ok does nothing.

Does the fstab file only run on bootup or is it supposed to affect devices that are mounted afterwards aswell?

---

### Post by ukripper on 2007-06-21
Can you post output of dmesg here.

use ```
dmesg | grep usb
```

Also could you post ```
lsusb
```

---

### Post by dentaku65 on 2007-06-21
Two things:

First option
edit your menu.lst grub config file 

Kubuntu
```
sudo kate /boot/grub/menu.lst
```

Ubuntu
```
sudo gedit /boot/grub/menu.lst
```

and add at the end of the kernel line

```
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=dc31275e-48c1-4c8c-b8cb-10e9877ca7af ro quiet splash
```

**irqpoll** entry

```
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=dc31275e-48c1-4c8c-b8cb-10e9877ca7af ro quiet splash irqpoll
```

Reboot your box

Or (second option)
```
sudo modprobe -r ehci_hcd && sudo modprobe ehci_hcd
```
every time you turn on your machine

---

