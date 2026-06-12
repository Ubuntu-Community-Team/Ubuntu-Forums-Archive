---
title: "Firewire drive no longer showing in /dev nor fdisk [Trusty] Ratoc Firedock FR-DK2"
date: 2015-02-06
forum: Hardware
---

### Post by philwhite on 2015-02-06
**Hardware:** 
[LIST]
[*]Ratocsystems Firedock FR-DK2 with one or two Maxtor IDE drives 
[*]SWEEX PCMCIA card with two USB and two Firewire connectors 
[/LIST]
**Definitely worked in the past:** With Hardy, the drives showed as /dev/sdb and /dev/sdc (I think) but I haven't used it for a couple of years

**Cannot see the drives now**: With either Precise or Trusty (just re-installed) I cannot see the drives.
[LIST]
[*]I am using the new Firewire stack but I may be loading it incorrectly or in the wrong sequence. Any advice would be greatly appreciated 
[/LIST]

uname -a
```
3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:37:48 UTC 2015 i686 i686 i686 GNU/Linux
```
lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```
After booting with either one or two drives connected and running, or if I start the drive(s) after booting ...

lspci | egrep 'firewire|ohci|1394'
```
02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
07:00.3 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
```
dmesg | egrep 'firewire|ohci|1394'
```
[    1.363013] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.363017] ohci-pci: OHCI PCI platform driver
[    1.363042] ohci-platform: OHCI generic platform driver
[    2.076154] firewire_ohci 0000:02:03.2: added OHCI v1.0 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[   17.608677] firewire_ohci 0000:07:00.3: enabling device (0080 -> 0083)
[   17.664133] firewire_ohci 0000:07:00.3: added OHCI v1.10 device as card 1, 4 IR + 4 IT contexts, quirks 0x11
```
lsmod | egrep 'firewire|ohci|1394'
```
firewire_ohci          35529  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
```
modprobe -v firewire_sbp2
```
insmod /lib/modules/3.13.0-45-generic/kernel/drivers/firewire/firewire-sbp2.ko 
modprobe: ERROR: could not insert 'firewire_sbp2': Operation not permitted
```
sudo modprobe -v firewire_sbp2
```
insmod /lib/modules/3.13.0-45-generic/kernel/drivers/firewire/firewire-sbp2.ko 
```
lsmod | egrep 'firewire|ohci|1394'
```
firewire_sbp2          18140  0 
firewire_ohci          35529  0 
firewire_core          61867  2 firewire_ohci,firewire_sbp2
crc_itu_t              12627  1 firewire_core
```

I think I have loaded the neccessary modules correctly above, but please tell me if I have got it wrong.
[LIST]
[*]Do I need to load some SCSI module? 
[*]Do I need to do something with udev? 
[/LIST]
However, I cannot see the drives.

ls -1 /dev | grep '^s' | tr '\n' ','
```
sda,sda1,sda2,sda5,sda6,sda7,sg0,shm,snapshot,snd,stderr,stdin,stdout,
```
sudo fdisk -lu    # shows only my internal drive
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb319b319

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS/exFAT
/dev/sda2        61433854   156299263    47432705    5  Extended
/dev/sda5        61433856    65339391     1952768   82  Linux swap / Solaris
/dev/sda6        94638080   156299263    30830592   83  Linux
/dev/sda7        65341440    94623743    14641152   83  Linux

Partition table entries are not in disk order
```

Attempting to mount sg0 does not work

sudo mount -vt vfat /dev/sg0 /media/firedock
```
mount: /dev/sg0 is not a block device
```
sudo mount -vt ext3 /dev/sg0 /media/firedock
```
mount: /dev/sg0 is not a block device
```

Apologies if I have formatted this message incorrectly. It is ages since I have posted here I had to register again, so I feel like a newbie again here.
Phil

---

