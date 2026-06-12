---
title: "GRUB don't start if 3114 SATA Raid Activated on MB"
date: 2007-01-16
forum: Hardware &amp; Laptops
---

### Post by pepere51 on 2007-01-16
Hi all,

I'm installing a new server configuration, and i'm not able to boot on if all SATA ctrl are activated.

_My configuration is:_

Athlon 64 3200+ / RAM 1 Gb
ASUS A8N-SLI-Deluxe
8 SATA disks :
[INDENT]On NVidia Sata Ctrl (Raid desactivated)
           [INDENT]- /dev/sda - 160Gb
                        [INDENT](80 Gb NTFS) Windows XP SP2 
                                      (80 Gb Raid 1/Ext3)  : 
                                                 [INDENT][INDENT]**/** (/dev/md0)
                                                                        **/home** (/dev/md1)
                                                                        **swap** (/dev/md2)[/INDENT][/INDENT][/INDENT]
           - /dev/sdb - 500Gb - Raid 1/Ext3 : (/dev/md3)
           - /dev/sdc - 160Gb
                        [INDENT](80 Gb Empty) 
                                      (80 Gb Raid 1/Ext3)  : 
                                                 [INDENT][INDENT]**/** (/dev/md0)
                                                                        **/home** (/dev/md1)
                                                                        **swap** (/dev/md2)[/INDENT][/INDENT][/INDENT]
           - /dev/sdd - 500Gb - Raid 1/Ext3 : (/dev/md3)[/INDENT]
 
      On Silicon Image 3114 SATA RAID Ctrl (Motherboard buil-in ctrl)
           [INDENT]- /dev/sde - 300Gb - Ext3
           - /dev/sdf - 320Gb - Ext3
           - /dev/sdg - 300Gb - Ext3
           - /dev/sdh - 320Go - Ext3[/INDENT][/INDENT]


Default boot HD in BIOS is /dev/sda (i tried with /dev/sdc too). Both have GRUB installed on.

All Raid 1 configurations are software ([FONT="Courier New"]mdadm[/FONT]).

GRUB don't run (so I can't boot on HD) if the second SATA Raid Ctrl (Silicon Image 3114 SATA RAID) is activated in the Motherboard BIOS.

If I boot in Rescue mode with the installation CD, all 8 disks are recognized.


If I boot on HD without Silicon Image 3114 SATA RAID Ctrl activated, the 4 disks of NVidia ctrl are available.

I use UBUNTU Edgy 6.10 AMD 64 Alternate

Here is my menu.lst
[FONT="Courier New"][INDENT]
default         0
timeout         10

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/md0 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/md0 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
# title         Microsoft Windows XP Professionnel
# root          (hd0,0)
# savedefault
# makeactive
# chainloader   +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title           Microsoft Windows XP Professionnel
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
[/INDENT][/FONT]

Here is my device.map
[FONT="Courier New"][INDENT]
(hd0)   /dev/sda
(hd1)   /dev/sdc
[/INDENT][/FONT]

Thanks for your help

Pepere

---

### Post by pepere51 on 2007-01-17
up

---

### Post by pepere51 on 2007-01-19
up again.

Is this problem complex or badly explained ?

---

