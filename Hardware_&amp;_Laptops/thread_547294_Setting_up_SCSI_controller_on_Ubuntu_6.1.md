---
title: "Setting up SCSI controller on Ubuntu 6.1"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by PerpsTherapy on 2007-09-09
Greetings to all.

I've got Ubuntu 6.1 (2.6.17-10-powerpc kernel) running on a G4 Power Mac box which I have recently just installed an old Adaptec SCSI controller attached to a number of hard drives into. It seems to me that the controller is being detected, as lspci yields the following:

```
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:0d.0 PCI bridge: Digital Equipment Corporation DECchip 21154 (rev 05)
0001:11:02.0 SCSI storage controller: Adaptec AHA-2940U2/U2W
0001:11:07.0 Class ff00: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:11:08.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:11:09.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:11:0a.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0002:21:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:21:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

```

I can't however, see anything related to the SCSI controller mentioned in fdisk -l:

```
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           57136719 @ 2018     ( 27.2G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                1494607 @ 57138737 (729.8M)  Linux swap

Block size=512, Number of Blocks=58633344
DeviceType=0x0, DeviceId=0x0

```

How would I got about setting up the SCSI controller so that I could access the disks that are attached to it?

Many thanks,

- PerpsTherapy.

---

### Post by PerpsTherapy on 2007-09-16
Update: 

From what I've read, aic7xxx can be used for the Adaptec SCSI controller. I modprobed it, but dmesg yields the following:

```

[  119.409959] aic7xxx: PCI17:2:0 MEM region 0x0 unavailable. Cannot memory map device.
[  119.409981] aic7xxx: PCI17:2:0 IO region 0x0[0..255] unavailable. Cannot map device.
[  119.410001] aic7xxx: probe of 0001:11:02.0 failed with error -12

```

Any ideas?

Many thanks,

- PerpsTherapy.

---

