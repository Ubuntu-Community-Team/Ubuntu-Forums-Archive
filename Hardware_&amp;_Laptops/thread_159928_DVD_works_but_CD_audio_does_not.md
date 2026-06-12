---
title: "DVD works but CD audio does not"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by syspeo on 2006-04-13
Hi,

I have ubuntu breezy distribution
kernel 2.6.10.686
I'have problem with DVD RW drive. No problem for to read DVD, but to read audio CD or data CD is impossible.

Some additional information :

@myworkstation:~$ dmesg

[4295022.242000] hdd: packet command error: error=0x30 { LastFailedSense=0x03 }
[4295022.242000] ide: failed opcode was: unknown
[4295022.242000] ATAPI device hdd:
[4295022.242000]   Error: Medium error -- (Sense key=0x03)
[4295022.242000]   (reserved error code) -- (asc=0x57, ascq=0x00)
[4295022.242000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4295022.242000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4295041.322000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4295041.322000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295041.400000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4295041.400000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

@myworkstation:~$ hdparm -i /dev/hdd

Model=TOSHIBA CD/DVDW SD-R5372, FwRev=TU53, SerialNo=354E507440
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Reserved:

 * signifies the current active mode

@myworkstation:~$ hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

I try to add "hdd=ide-scsi" at last /boot/grub/menu.lst

after reboot, problem is always present.

any suggestions ?
:-?

---

