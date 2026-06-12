---
title: "Upgraded to Intrepid Ibex and now can't boot"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by [z]er0 HP on 2008-12-11
As the title Describes I'm having trouble after I used the Update manager to upgrade. It prompted me to restart, so I did. It was starting up normally, BIOS, GRUB, then it came up with an error message on a black terminal screen.
```

usplash: no usable theme found for 1280x1024
screen init failed

gave up waiting for root device. common problems:
-boot args (cat /proc/cmdline)
-check rootdelay=(did the system wait long enough?)
-check root=(did the system wait for the right device?) 
-missing modules (cat /proc/modules; is dev)

ALERT! /dev/disk/by-uuid/07cdf0c-25f1-4db1-a213-d44bcd3efbdd does not exist. dropping to shell!


Busybox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs) [  61.156011] ata6: SRST failed (errno=-16)
(initramfs)

```

I have absolutely no idea where to go from here and would appreciate any help. Thanks in advance

---

### Post by Michael.Godawski on 2008-12-11
Have seen the exact error message on the Absolute Beginners Forum few days ago. The issue was a hard drive failure when I remember correctly (the hard drive was old or something). 

Have you done a back-up of your important data? If yes then I would suggest a clean fresh install. If no here you can read how to access the hard drive via the live CD.

[LIST]
[*][http://godawski.oxyhost.com/accesshd.html](http://godawski.oxyhost.com/accesshd.html)
[/LIST]
Are you able to boot into recovery mode?

---

### Post by caljohnsmith on 2008-12-11
Have you tried booting with an older kernel listed in your Grub menu? I've seen some people in the forums getting those "ALERT! /dev/disk/by-uuid/xxxx" errors with the new kernel upgrade. If booting a previous kernel doesn't work, how about trying this: when you get the Grub menu on start up, select the Ubuntu entry you want to boot, press "e" to edit it, select the "kernel" line, press "e" to edit it, and then add at the end of the line "rootdelay=120" similar to:
```
kernel  /boot/vmlinuz-2.6.27-9-generic root=UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 ro quiet splash [COLOR="Blue"]rootdelay=120[/COLOR]
```
See if that helps. Let me know how it goes. :)

---

### Post by ronnyteve on 2008-12-11
HI, my english is not too good, i am sorry...

I installed Intrepid Ibex in a ibm computer that has windows xp, so, i have windows and ubuntu now...

my problem is in the boot... because appear messages such as those described above.

> 
[    9.036767] Driver 'sd' needs updating - please use bus_type methods
[   13.564018] ata1: SRST failed (errno=-16)
[   18.760017] ata1: link is slow to respond, please be patient (ready=0)
[   23.576020] ata1: SRST failed (errno=-16)
[   28.772014] ata1: link is slow to respond, please be patient (ready=0)
[   53.628435] ata1.00: ATA-6: WDC WD800BB-23FJA0, 13.03G13, max UDMA/100
[   53.628440] ata1.00: 156312576 sectors, multi 16: LBA 
[   53.636381] ata1.00: configured for UDMA/100
[   53.984664] ata2.00: ATAPI: LTN486S, YUS8, max UDMA/33
[   53.984684] ata2.01: ATAPI: DVDRW   20X20X12X, 6A31, max UDMA/66
[   53.992373] ata2.00: configured for UDMA/33
[   54.024227] ata2.01: configured for UDMA/66
[   54.024360] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-23FJ 13.0 PQ: 0 ANSI: 5
[   54.024609] scsi 0:0:0:0: Attached scsi generic sg1 type 0
[   54.025440] scsi 1:0:0:0: CD-ROM            LITEON   CD-ROM LTN486S   YUS8 PQ: 0 ANSI: 5
[   54.025655] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   54.026955] scsi 1:0:1:0: CD-ROM            DVDRW    20X20X12X        6A31 PQ: 0 ANSI: 5
[   54.027177] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   54.027235] e1000 0000:03:0b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   54.028670] sd 2:0:0:0: [sda] 1993649 512-byte hardware sectors (1021 MB)
[   54.029415] sd 2:0:0:0: [sda] Write Protect is off
[   54.029418] sd 2:0:0:0: [sda] Mode Sense: 00 c0 00 00
[   54.029421] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   54.030792] sd 2:0:0:0: [sda] 1993649 512-byte hardware sectors (1021 MB)
[   54.031289] sd 2:0:0:0: [sda] Write Protect is off
[   54.031293] sd 2:0:0:0: [sda] Mode Sense: 00 c0 00 00
[   54.031295] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   54.031353]  sda:
[   54.032757] sd 2:0:0:0: [sda] Attached SCSI removable disk
[   54.033916] sd 0:0:0:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[   54.033944] sd 0:0:0:0: [sdb] Write Protect is off
[   54.033947] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   54.033982] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.034092] sd 0:0:0:0: [sdb] 156312576 512-byte hardware sectors (80032 MB)
[   54.034111] sd 0:0:0:0: [sdb] Write Protect is off
[   54.034115] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   54.034148] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   54.034153]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 >
[   54.080821] sd 0:0:0:0: [sdb] Attached SCSI disk
[   54.386012] e1000: 0000:03:0b.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:60:24:fd:b1
[   54.654479] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   54.717230] Driver 'sr' needs updating - please use bus_type methods
[   54.723155] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   54.723161] Uniform CD-ROM driver Revision: 3.20
[   54.723295] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   54.728299] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   54.728445] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   67.378157] PM: Starting manual resume from disk
[   67.378163] PM: Resume from partition 8:22
[   67.378165] PM: Checking hibernation image.
[   67.378399] PM: Resume from disk failed.
[   67.427885] kjournald starting.  Commit interval 5 seconds
[   67.427906] EXT3-fs: mounted filesystem with ordered data mode.
[   74.034849] udevd version 124 started
[   74.636216] Linux agpgart interface v0.103
[   74.712222] agpgart-intel 0000:00:00.0: Intel 865 Chipset


but i can enter in ubuntu because appear a shell i press CONTROL-D and become to star ok.. :)

something detail of my computer are:

> 
    Placa base:

      Tipo de procesador                                Intel Pentium 4, 2800 MHz (21 x 133)

      Nombre de la Placa Base                           IBM 818833S

      Chipset de la Placa Base                          Intel Springdale-G i865G

      Memoria del Sistema                               1270 MB  (DDR SDRAM)

      Tipo de BIOS                                      Phoenix (07/06
/05)


    DMI:

      DMI Distribuidor de la BIOS                       IBM

      DMI Versión de la BIOS                            2AKT51ASP

      DMI Fabricante del Sistema                        IBM

      DMI Nombre del Sistema                            818833S


Disco duro                                        WDC WD800BB-23FJA0  (74 GB, IDE)


This is the first distribution that can see my hard drives, because neither versions 7.04, 7.10 and 8.04 as detected in the live mode.

Thank you very much, Ronny

---

### Post by [z]er0 HP on 2008-12-11
I can't boot into recovery mode, the hard drive is only about 6 months old and i would see no reason for it to fail. I don't have backups of a large amount of my data but I will pull out another hard drive and a livecd. This is an extreme pain in the *** as any other ubuntu user would know the amount of hours go into customization of the fresh install. If anyone has any ideas as to how to fix this I would be eternally greatful.

Edit:
I tried adding the rootdelay=120 onto that line and still no cigar.

---

### Post by [z]er0 HP on 2008-12-11
I managed to get it to boot by typing 'exit' at the prompt.
I'm currently running ubuntu now and I need instructions about which files i should modify so this does not happen again.

Output from fdisk -l
```

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe454e454

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59573   478520091   83  Linux
/dev/sda2           59574       60801     9863910    5  Extended
/dev/sda5           59574       60801     9863878+  82  Linux swap / Solaris

```

/boot/grub/menu.lst
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=070cdf0c-25f1-4db1-a213-d44bcd3efbdd ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=070cdf0c-25f1-4db1-a213-d44bcd3efbdd ro quiet splash vga=795 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=070cdf0c-25f1-4db1-a213-d44bcd3efbdd ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by ronnyteve on 2008-12-11
Do you tray press CTRL-D after that apear 

> Busybox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs) [  61.156011] ata6: SRST failed (errno=-16)
(initramfs)

it works for me, but it is a temporary solution...

i don't know how fixed yet... i need help  :sad:

---

