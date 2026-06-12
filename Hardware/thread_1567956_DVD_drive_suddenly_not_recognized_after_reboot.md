---
title: "DVD drive suddenly not recognized after reboot"
date: 2010-09-04
forum: Hardware
---

### Post by mjf on 2010-09-04
I'm using 9.04.  Basically, I rebooted and now it seems the DVD drive is no longer detected.  The device /dev/dvd used to exist but now does not.  Devices like /dev/cdrom and /dev/scd0 also do not exist.

I made no major change before rebooting except for typical updates that pop up automatically in Update Manager.

I've tried both having a DVD inside and not inside the tray during bootup, but no effect.

I've verified that the DVD drive is successfully recognized by BIOS and Windows.

Any ideas how to proceed?

---

### Post by S.R on 2010-09-04
```
lshw -short
```

Please.

---

### Post by mjf on 2010-09-04
```
$ sudo lshw -short
H/W path              Device     Class          Description
===========================================================
                                 system         System Product Name
/0                               bus            A8V
/0/0                             memory         64KiB BIOS
/0/4                             processor      AMD Athlon(tm) 64 Processor 3200+
/0/4/5                           memory         128KiB L1 cache
/0/4/6                           memory         512KiB L2 cache
/0/39                            memory         2GiB System Memory
/0/39/0                          memory         1GiB DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/39/1                          memory         1GiB DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/100                           bridge         K8T800Pro Host Bridge
/0/100/1                         bridge         VT8237 PCI bridge [K8T800/K8T890 South]
/0/100/1/0                       display        NV44A [GeForce 6200]
/0/100/a              eth0       network        88E8001 Gigabit Ethernet Controller
/0/100/f                         storage        VIA VT6420 SATA RAID Controller
/0/100/f.1            scsi2      storage        VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
/0/100/f.1/0.0.0      /dev/sda   disk           80GB ST380013A
/0/100/f.1/0.0.0/1    /dev/sda1  volume         20GiB Windows NTFS volume
/0/100/f.1/0.0.0/2    /dev/sda2  volume         7169MiB EXT3 volume
/0/100/f.1/0.0.0/3    /dev/sda3  volume         22GiB Extended partition
/0/100/f.1/0.0.0/3/5  /dev/sda5  volume         2047MiB Linux swap / Solaris partition
/0/100/f.1/0.0.0/3/6  /dev/sda6  volume         20GiB Linux filesystem partition
/0/100/f.1/0.0.0/4    /dev/sda4  volume         25GiB Windows FAT volume
/0/100/f.1/0.1.0      /dev/sdb   disk           250GB WDC WD2500JB-00G
/0/100/f.1/0.1.0/1    /dev/sdb1  volume         58GiB Windows NTFS volume
/0/100/f.1/0.1.0/2    /dev/sdb2  volume         173GiB Extended partition
/0/100/f.1/0.1.0/2/5  /dev/sdb5  volume         57GiB HPFS/NTFS partition
/0/100/f.1/0.1.0/2/6  /dev/sdb6  volume         56GiB HPFS/NTFS partition
/0/100/f.1/0.1.0/2/7  /dev/sdb7  volume         59GiB FAT16 partition
/0/100/10                        bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.4                      bus            USB 2.0
/0/100/11                        bridge         VT8237 ISA bridge [KT600/K8T800/K8T890 South]
/0/100/11.5                      multimedia     VT8233/A/8235/8237 AC97 Audio Controller
/0/100/11.6                      communication  AC'97 Modem Controller
/0/101                           bridge         K8T800Pro Host Bridge
/0/102                           bridge         K8T800Pro Host Bridge
/0/103                           bridge         K8T800Pro Host Bridge
/0/104                           bridge         K8T800Pro Host Bridge
/0/105                           bridge         K8T800Pro Host Bridge
/0/106                           bridge         K8 [Athlon64/Opteron] HyperTransport Technology Configuration
/0/107                           bridge         K8 [Athlon64/Opteron] Address Map
/0/108                           bridge         K8 [Athlon64/Opteron] DRAM Controller
/0/109                           bridge         K8 [Athlon64/Opteron] Miscellaneous Control
/1                    pan0       network        Ethernet interface

```

---

### Post by S.R on 2010-09-05
Two things I can think of to try.

1.```
 sudo apt-get update
```  THEN   ```
sudo apt-get upgrade
```2. I am guessing you have GRUB installed. You can try booting an older kernel version to see if it is a kernel problem.

I had this problem on my custom rig I built. It worked then it stopped and then one day it just started working again.

---

### Post by S.R on 2010-09-06
Another fix I found that worked for some from launchpad:

```
sudo gedit /etc/modules
```

and below the all the "#" add these three lines

```
libata
ata_piix
piix
```


Save and reboot.

---

