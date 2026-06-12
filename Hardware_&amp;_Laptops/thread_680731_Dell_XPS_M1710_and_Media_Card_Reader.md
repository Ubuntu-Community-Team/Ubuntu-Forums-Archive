---
title: "Dell XPS M1710 and Media Card Reader"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by mascer on 2008-01-28
first, me=total new linux noob, so have patience with me ;)

I finally had the guts to delete WindowsXP (main reasons= Tired of M$ and SecondLife has an alpha client which is more stable than the windows one :P ) I replaced XP with Ubuntu 7.10 and all current updates are installed.

I got a problem with my media card reader, it doesnt detect that i put in a Sony memoryStickProDuo with SD-convertor. With XP it was detected as normal external storage (SD).

Anyone has an idea?? I'm in a bit of a hurry..i just beame farther and can't get pics onto the WWW :)

Greetings all and thnx in advanced!

---

### Post by mascer on 2008-01-28
Some more info, no clue if that helps :confused:

I just tried a mini-SD card in a Mini-SD-to-SD-convertor and that works fine. I could add docs and pics to it.

> df (with no memory cards)

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             30763896   9714736  19486440  34% /
varrun                 1037412        88   1037324   1% /var/run
varlock                1037412         0   1037412   0% /var/lock
udev                   1037412       100   1037312   1% /dev
devshm                 1037412         0   1037412   0% /dev/shm
lrm                    1037412     34696   1002716   4% /lib/modules/2.6.22-14-generic/volatile

> df (with mini-SD card)

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             30763896   9714924  19486252  34% /
varrun                 1037412        88   1037324   1% /var/run
varlock                1037412         0   1037412   0% /var/lock
udev                   1037412       108   1037304   1% /dev
devshm                 1037412         0   1037412   0% /dev/shm
lrm                    1037412     34696   1002716   4% /lib/modules/2.6.22-14-generic/volatile
/dev/mmcblk0p1          494328      4300    490028   1% /media/disk

> df (with sony memory stick)
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             30763896   9714916  19486260  34% /
varrun                 1037412        88   1037324   1% /var/run
varlock                1037412         0   1037412   0% /var/lock
udev                   1037412       100   1037312   1% /dev
devshm                 1037412         0   1037412   0% /dev/shm
lrm                    1037412     34696   1002716   4% /lib/modules/2.6.22-14-generic/volatile

> lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)

---

### Post by mascer on 2008-02-05
my 'first cup of ubuntu' isnt tasting very well :shock:

---

