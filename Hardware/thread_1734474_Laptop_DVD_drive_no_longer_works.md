---
title: "Laptop DVD drive no longer works"
date: 2011-04-20
forum: Hardware
---

### Post by ExecutorE on 2011-04-20
I'm updating regularly, and between today and Monday (two days ago) my internal dvd drive (on a laptop) has stopped responding. Upon inserting a disc, I get this on dmesg:

```
[  252.568353] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[  252.568379] sr: Sense Key : Hardware Error [current] 
[  252.568387] sr: Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  252.574586] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  252.574596] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  252.574606] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  252.574618] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  252.574639] end_request: I/O error, dev sr0, sector 0
[  252.580455] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  252.580464] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  252.580474] sr 0:0:0:0: [sr0] ASC=0x21 ASCQ=0x10
[  252.580488] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  252.580512] end_request: I/O error, dev sr0, sector 0

```

and this on the desktop:

```
"Method "Mount" with signature "ssas" on interface "org.freedesktop.Hal.Device.Volume" doesn't exist"
```

Any suggestions what that is?

thanks,

EE
PS- before I turned the laptop of and cold-restarted, I was also getting a lot of errors about a system message bus refusing the connection, causing synaptic, gconf-settings, and a bunch of other programs to freeze. Is that related?
PPS- lest anybody think it's just a problem with DVDs: I can't play audio CDs, either. VLC segfaults if I try to play a disc.

---

### Post by ExecutorE on 2011-04-21
UPDATE:

upon reboot, here is what dmesg says whenever I try to probe the drive (say, srtarting k3b):

```
[ 2143.613639] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 2143.613653] ata1.00: unexpected or too much trailing data buf=60 cur=60 bytes=60
[ 2143.613664] sr 0:0:0:0: [sr0] CDB: Mode Select(10): 55 10 00 00 00 00 00 00 3c 00
[ 2143.613701] ata1.00: cmd a0/00:00:00:3c:00/00:00:00:00:00/a0 tag 0 pio 60 out
[ 2143.613704]          res 58/00:00:3c:3c:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[ 2143.613712] ata1.00: status: { DRDY DRQ }
[ 2143.613754] ata1: soft resetting link
[ 2143.793174] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c7c7) ACPI=0x701f (60:600:0x13)
[ 2143.833135] ata1.00: configured for UDMA/33
[ 2143.839497] ata1: EH complete

```

I have read a couple places that sleep mode sometimes does this to drives with APCI/APIC enabed; could this be a problem with a recent kernel?

Thanks,

EE

---

