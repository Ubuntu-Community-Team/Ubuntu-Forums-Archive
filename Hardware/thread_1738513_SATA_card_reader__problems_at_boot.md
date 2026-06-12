---
title: "SATA card reader : problems at boot"
date: 2011-04-24
forum: Hardware
---

### Post by mdtsandman on 2011-04-24
[FONT=Courier New]Ubuntu 10.10
2.6.35-28-server

I have an Addonics multicard reader connected via a Silicon Image 3114 SATA controller.  According to the documentation provided with both the device and the controller, this combination should be seen by the kernel as a hot-swappable fixed disk.

When booted with CF media in the reader, the boot process unfolds normally and I am able to mount the media as expected.  When I unmount a card, then remove it physically, the device disappears in[/FONT] /dev/disk/by-id[FONT=Courier New]

When a new card is inserted, I need to run

[/FONT]```
sudo udevadm trigger
```[FONT=Courier New]

to get the new card detected, but it is then mountable.

When booted without any media in the reader, the system won't boot properly.  It appears that the device mapper is trying to identify and map the drive, but thinks there is a problem with the device.

Is there a way to have the drive ignored in the boot process?  I have tried rebuilding the initial ramdisk (using the process [here]("http://ubuntuforums.org/showthread.php?t=1626172")) with a udev rule like this:

[/FONT]```
SUBSYSTEM=="block", ATTRS{MODEL}=="Addonics_CompactFlash", ENV{DM_UDEV_DISABLE_DISK_RULES_FLAG}:="1", OPTIONS="last_rule"
```[FONT=Courier New]

with no success.

Any help would be greatly appreciated!  Thanks in advance.


[/FONT]

---

### Post by mdtsandman on 2011-04-24
Addendum - tail end of (many similat) kernel errors at boot with no media in reader:

ata7.00: cmd c8/00:08:f8:ff:01/00:00:00:00:00/e0 tag 0 dma 4096 in
               res 51/02:08:f8:ff:01/00:00:00:00:00/e0 Emask 0x1 (device error)
ata7.00: status: { DRDY ERR }
ata7.00: configured for UDMA/100
ata7: EH complete
ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata7.00: BMDMA2 stat 0x80d0009
ata7.00: failed command: READ DMA
ata7.00: cmd c8/00:08:f8:ff:01/00:00:00:00:00/e0 tag 0 dma 4096 in
               res 51/02:08:f8:ff:01/00:00:00:00:00/e0 Emask 0x1 (device error)
ata7.00: status: { DRDY ERR }
device-mapper: ioctl: device doesn't appear to be in the dev hash table.
ata7.00 configured for UDMA/100
sd 6:0:0:0: [sdc] Unhandled sense code
sd 6:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
sd 6:0:0:0: [sdc] Sense Key : Hardware Error [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
     72 04 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00
     00 01 ff f8
sd 6:0:0:0: [sdc] Add. Sense: No additional sense information
sd 6:0:0:0: [CDB: Read(10): 28 00 00 01 ff f8 00 00 08 00
end_request: I/O error, dev sdc, sector 131064
Buffer I.O error on device sdc, logical block 16383 
ata7: EH complete
device-mapper: table: 251:2: mirror: Device lookup failure
device-mapper: ioctl: error adding target to table
device-mapper: ioctl: device doesn't appear to be in the dev hash table.

---

### Post by mdtsandman on 2011-05-01
bump (still no joy with this)

---

