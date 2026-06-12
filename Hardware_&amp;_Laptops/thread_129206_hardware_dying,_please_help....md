---
title: "hardware dying, please help..."
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by muszek on 2006-02-13
Hi,

I'm talking about a 120 GB drive, split into two partitions - one ext3 (I think, might be reiserfs) and one fat32 (that partition is being written to under windows every half a year or so... I figured it's just easier to use fat32 for it).
That's a hard drive i use for storing mp3 for my fathers jukeboxes (linux-powered  machines that play music in pubs), so it travels a lot.  Lately it started to be a little noisy.  Then the first partition (hda1) went wrong, but fsck helped (I think I lost some not important files, though).  On the next boot, it didn't help... but the second partition (hda5) still lived.  On the next boot, it also died.

fsck on the first one:
```
sudo fsck /dev/hda1
Password:
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda1: Attempt to read block from filesystem resulted in short read while reading block 524

/dev/hda1: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda1
```

and on the second:
```
sudo fsck /dev/hda5
fsck 1.38 (30-Jun-2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Read 512 bytes at 0:Input/output error

```

here's dmesg:
```
sudo dmesg
Password:
, dev hda, sector 114688098
[4297208.612000] Buffer I/O error on device hda5, logical block 0
[4297217.875000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297217.875000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297217.875000] ide: failed opcode was: unknown
[4297217.875000] end_request: I/O error, dev hda, sector 114688099
[4297217.875000] Buffer I/O error on device hda5, logical block 1
[4297226.987000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297226.987000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297226.987000] ide: failed opcode was: unknown
[4297226.987000] end_request: I/O error, dev hda, sector 114688098
[4297226.987000] Buffer I/O error on device hda5, logical block 0
[4297236.271000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297236.271000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297236.271000] ide: failed opcode was: unknown
[4297236.271000] end_request: I/O error, dev hda, sector 114688099
[4297236.271000] Buffer I/O error on device hda5, logical block 1
[4297245.947000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297245.947000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297245.947000] ide: failed opcode was: unknown
[4297245.947000] end_request: I/O error, dev hda, sector 114688098
[4297245.947000] Buffer I/O error on device hda5, logical block 0
[4297258.461000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297258.461000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297258.461000] ide: failed opcode was: unknown
[4297258.461000] end_request: I/O error, dev hda, sector 114688099
[4297258.461000] Buffer I/O error on device hda5, logical block 1
[4297267.344000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297267.344000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297267.344000] ide: failed opcode was: unknown
[4297267.344000] end_request: I/O error, dev hda, sector 114688098
[4297267.344000] Buffer I/O error on device hda5, logical block 0
[4297279.941000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297279.941000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297279.942000] ide: failed opcode was: unknown
[4297279.942000] end_request: I/O error, dev hda, sector 114688099
[4297279.942000] Buffer I/O error on device hda5, logical block 1
[4297289.895000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297289.895000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297289.895000] ide: failed opcode was: unknown
[4297289.895000] end_request: I/O error, dev hda, sector 114688098
[4297289.895000] Buffer I/O error on device hda5, logical block 0
[4297301.992000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297301.992000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297301.992000] ide: failed opcode was: unknown
[4297301.992000] end_request: I/O error, dev hda, sector 114688099
[4297301.992000] Buffer I/O error on device hda5, logical block 1
[4297310.870000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297310.870000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297310.870000] ide: failed opcode was: unknown
[4297310.870000] end_request: I/O error, dev hda, sector 114688098
[4297310.870000] Buffer I/O error on device hda5, logical block 0
[4297320.218000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297320.218000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297320.218000] ide: failed opcode was: unknown
[4297320.218000] end_request: I/O error, dev hda, sector 114688099
[4297320.218000] Buffer I/O error on device hda5, logical block 1
[4297434.698000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297434.698000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297434.698000] ide: failed opcode was: unknown
[4297434.698000] end_request: I/O error, dev hda, sector 114688098
[4297434.698000] Buffer I/O error on device hda5, logical block 0
[4297443.872000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297443.872000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297443.872000] ide: failed opcode was: unknown
[4297443.872000] end_request: I/O error, dev hda, sector 114688099
[4297443.872000] Buffer I/O error on device hda5, logical block 1
[4297453.276000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297453.276000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688098
[4297453.276000] ide: failed opcode was: unknown
[4297453.276000] end_request: I/O error, dev hda, sector 114688098
[4297453.276000] Buffer I/O error on device hda5, logical block 0
[4297465.324000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4297465.324000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688099
[4297465.324000] ide: failed opcode was: unknown
[4297465.324000] end_request: I/O error, dev hda, sector 114688099
[4297465.324000] Buffer I/O error on device hda5, logical block 1
[4299658.564000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299658.564000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4255, high=0, low=4255, sector=4255
[4299658.564000] ide: failed opcode was: unknown
[4299658.564000] end_request: I/O error, dev hda, sector 4255
[4299658.564000] Buffer I/O error on device hda1, logical block 1048
[4299669.284000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299669.284000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4261, high=0, low=4261, sector=4259
[4299669.284000] ide: failed opcode was: unknown
[4299669.284000] end_request: I/O error, dev hda, sector 4259
[4299669.284000] Buffer I/O error on device hda1, logical block 1049
[4299680.001000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299680.001000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4255, high=0, low=4255, sector=4255
[4299680.001000] ide: failed opcode was: unknown
[4299680.001000] end_request: I/O error, dev hda, sector 4255
[4299680.001000] Buffer I/O error on device hda1, logical block 1048
[4299691.686000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299691.686000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4261, high=0, low=4261, sector=4259
[4299691.686000] ide: failed opcode was: unknown
[4299691.686000] end_request: I/O error, dev hda, sector 4259
[4299691.686000] Buffer I/O error on device hda1, logical block 1049
[4299733.961000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[4299733.962000] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
[4299733.987000] cdrom: open failed.
[4299734.005000] cdrom: open failed.
[4299746.172000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299746.172000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299746.172000] ide: failed opcode was: unknown
[4299746.172000] end_request: I/O error, dev hda, sector 114688096
[4299746.172000] Buffer I/O error on device hda, logical block 14336012
[4299757.902000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299757.902000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299757.902000] ide: failed opcode was: unknown
[4299757.902000] end_request: I/O error, dev hda, sector 114688096
[4299757.902000] Buffer I/O error on device hda, logical block 14336012
[4299769.581000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299769.581000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299769.581000] ide: failed opcode was: unknown
[4299769.581000] end_request: I/O error, dev hda, sector 114688096
[4299769.581000] Buffer I/O error on device hda, logical block 14336012
[4299780.957000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299780.957000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299780.957000] ide: failed opcode was: unknown
[4299780.957000] end_request: I/O error, dev hda, sector 114688096
[4299780.957000] Buffer I/O error on device hda, logical block 14336012
[4299792.014000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299792.014000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299792.014000] ide: failed opcode was: unknown
[4299792.014000] end_request: I/O error, dev hda, sector 114688096
[4299792.014000] Buffer I/O error on device hda, logical block 14336012
[4299802.663000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299802.663000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299802.663000] ide: failed opcode was: unknown
[4299802.663000] end_request: I/O error, dev hda, sector 114688096
[4299802.663000] Buffer I/O error on device hda, logical block 14336012
[4299814.695000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299814.695000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299814.695000] ide: failed opcode was: unknown
[4299814.695000] end_request: I/O error, dev hda, sector 114688096
[4299814.695000] Buffer I/O error on device hda, logical block 14336012
[4299826.676000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299826.676000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299826.676000] ide: failed opcode was: unknown
[4299826.676000] end_request: I/O error, dev hda, sector 114688096
[4299826.676000] Buffer I/O error on device hda, logical block 14336012
[4299836.992000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299836.992000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299836.992000] ide: failed opcode was: unknown
[4299836.992000] end_request: I/O error, dev hda, sector 114688096
[4299836.992000] Buffer I/O error on device hda, logical block 14336012
[4299848.373000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299848.373000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299848.373000] ide: failed opcode was: unknown
[4299848.373000] end_request: I/O error, dev hda, sector 114688096
[4299848.373000] Buffer I/O error on device hda, logical block 14336012
[4299857.375000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299857.375000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299857.375000] ide: failed opcode was: unknown
[4299857.375000] end_request: I/O error, dev hda, sector 114688096
[4299857.375000] Buffer I/O error on device hda, logical block 14336012
[4299868.255000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299868.256000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299868.256000] ide: failed opcode was: unknown
[4299868.256000] end_request: I/O error, dev hda, sector 114688096
[4299868.256000] Buffer I/O error on device hda, logical block 14336012
[4299879.886000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299879.886000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299879.886000] ide: failed opcode was: unknown
[4299879.886000] end_request: I/O error, dev hda, sector 114688096
[4299879.886000] Buffer I/O error on device hda, logical block 14336012
[4299890.927000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299890.927000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299890.927000] ide: failed opcode was: unknown
[4299890.927000] end_request: I/O error, dev hda, sector 114688096
[4299890.927000] Buffer I/O error on device hda, logical block 14336012
[4299902.836000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299902.837000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299902.837000] ide: failed opcode was: unknown
[4299902.837000] end_request: I/O error, dev hda, sector 114688096
[4299902.837000] Buffer I/O error on device hda, logical block 14336012
[4299913.227000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299913.227000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299913.227000] ide: failed opcode was: unknown
[4299913.227000] end_request: I/O error, dev hda, sector 114688096
[4299913.227000] Buffer I/O error on device hda, logical block 14336012
[4299925.416000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299925.416000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299925.416000] ide: failed opcode was: unknown
[4299925.416000] end_request: I/O error, dev hda, sector 114688096
[4299925.416000] Buffer I/O error on device hda, logical block 14336012
[4299937.528000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299937.528000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299937.528000] ide: failed opcode was: unknown
[4299937.528000] end_request: I/O error, dev hda, sector 114688096
[4299937.528000] Buffer I/O error on device hda, logical block 14336012
[4299945.700000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299945.700000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299945.700000] ide: failed opcode was: unknown
[4299945.700000] end_request: I/O error, dev hda, sector 114688096
[4299945.700000] Buffer I/O error on device hda, logical block 14336012
[4299954.726000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4299954.726000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=114688099, high=6, low=14024803, sector=114688096
[4299954.726000] ide: failed opcode was: unknown
[4299954.726000] end_request: I/O error, dev hda, sector 114688096
[4299954.726000] Buffer I/O error on device hda, logical block 14336012
[4300200.316000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4300200.316000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4300200.413000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4300200.413000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

```

I know I should say "bye" to this hdd, but I really do care about data that's on it (I will not be able to access source hdd with all those mp3's for the next several days and my father needs them tonight).  Is there anything I can do?

---

### Post by Jedeye on 2006-02-13
Im still new to ubuntu/linux but could you boot up using the live cd, mount your partitions, and move the files to another drive or storage device?

---

### Post by Zimmer on 2006-02-13
Post #7 here may help......
[http://ubuntuforums.org/showthread.php?t=128910&highlight=recover+data](http://ubuntuforums.org/showthread.php?t=128910&highlight=recover+data)

---

### Post by muszek on 2006-02-13
but it's not hdd that ubuntu is booted from... it's my second hard drive.  fsck fails.

---

