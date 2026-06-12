---
title: "DVD drive recognized by Windows but not Ubuntu"
date: 2011-02-11
forum: Hardware
---

### Post by mjf on 2011-02-11
Hello,

I am running Lucid 10.04 Desktop.  My Samsung CDRW/DVD SM-352B is not recognized at all by Linux, but it works fine when I boot into Windows.  Any ideas how to debug this?

Here is the output of lshw:

```
% lshw -short
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
/0/100/f.1            scsi3      storage        VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
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
```

---

### Post by P4man on 2011-02-11
If its a sata dvd writer, then check in the bios if you can configure sata mode for EHCI or compatibility mode.
(note that changing these values for the harddisk, may make windows bluescreen).

---

### Post by mjf on 2011-02-11
> **P4man said:**
> If its a sata dvd writer, then check in the bios if you can configure sata mode for EHCI or compatibility mode.
(note that changing these values for the harddisk, may make windows bluescreen).

Thanks for the idea.  This is just a normal IDE drive.  I did look through BIOS for options and set the IDE device from "Auto" to "CDROM" but there was no effect.

---

### Post by mjf on 2011-02-12
I just upgraded the firmware using a Windows executable from Samsung's site, but no luck in Linux still.

Is there any way to debug this problem?  Examine logs or something?

---

