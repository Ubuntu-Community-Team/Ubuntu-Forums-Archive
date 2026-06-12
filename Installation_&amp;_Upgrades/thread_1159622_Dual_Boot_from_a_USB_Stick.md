---
title: "Dual Boot from a USB Stick?"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by dschmutz on 2009-05-14
I installed Ubuntu 9.04 on my computer at work in a dual boot configuration with Windows XP using Grub as the boot loader.  It worked great.  Then the company IT department came along and encrypted our computers using McAfee encryption.  This installed its own MBR which starts the encryption software and then boots Windows XP.  My Linux partitions are still intact (not encrypted), since I can access them if I boot from the Ubuntu Live CD.  But I don't know how to boot Linux from these partitions.  I didn't save the MBR and anyway I can't interfer with the McAfee MBR so I can't replace it anyway.  I thought to use the windows boot loader to send me to the linux partition.  I copied the MBR from another computer on which I dual boot XP and Ubuntu.  But it just prints Grub on a black screen and stops.  I'd use Wubi, but the information says it doesn't support encrypted disks.

I thought I might be able to boot to a USB stick and then select XP using the MBR on the hard drive or select Ubuntu on another partition.  But I don't know how to do this.  All I have found so far is the live cd that wants to run linux from the stick or boot the hard drive which means WinXP.  Can someone tell me how to get a stick to alow me to select either MBR on the hard drive or the linux partition?

Doug Schmutz

---

### Post by snakt on 2009-07-26
I think your best option is to install grub onto a usb so you can reconfigure it easily, using grub to load ubuntu from the usb and the boot loader on the pc to access windows.

Ye google will show there is a tool for windows wich will allow you to install and configure grub for a usb and save configs in the MBR? (i think it was a little while ago) so u can still use your regular file whore usb, just modify the MBR

i may be wrong about the MBR only part but search it up, as i have had grub running on a usb before attemping to dual boot dos and live ubuntu.

It was a fail :(

Could never get grub to find the linux partition and i gave up.

---

### Post by snakt on 2009-07-26
i just unberried the usb.

Grub resides in the MBR but the config is in 1 file named MENU.LST

this was how i had my usb config (i just unberried it)

```
default 1
timeout 30
splashimage (hd0,0)/Grub/linuxinside.xpm.gz
fallback 1

title load N DOS Disk
rootnoverify (hd0,0)
chainloader +1
makeactive
boot

title Load N Ubuntu 8.10 Live Disk
chainloader +1
boot (hd0,1)
```

Remember: when booting from a usb it then becomes the initial hdd so what was once:

```
0,1 or 2,3
```

Becomes

```
1,1 or 3,3
```

---

