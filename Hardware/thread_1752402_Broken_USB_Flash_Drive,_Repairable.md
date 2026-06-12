---
title: "Broken USB Flash Drive, Repairable?"
date: 2011-05-07
forum: Hardware
---

### Post by Robert1995 on 2011-05-07
I've had this broken USB Flash Drive with me a while now. It was broken during general use... it was plugged in and working one minute... dead the next. So i think it's down to corruption rather then physical damage.

The Story:
I got this 16GB Memory Stick (Kingston) and put a tonne of crap on it such as movies, music and portable apps... as I was playing a music track with VLC I commonly got the error that the file was not fond (half-way through playback) this was resolved when I reconnected the device which is occasionally occured again.

Anyway, one day it decided to die... Now it no longer appears as a device... HOWEVER it does appear in my Disk Utility as a GENERIC USB Mass Storage .. The device has power as the green light flashes and other than that... I'm clueless.

Here's what the disk utility says.
Model: GENERIC USB Mass Stoarge
Firmware Version: 1.00
Location: -
Write Cache: -
Capacity: 0.0kB (0 bytes)
Partitoning: Not Partitioned
Serial Number: 001372997D4BF011D6290CF1
World Wide Name: -
Device: /dev/sdf
Rotation Rate: -
Connection: USB at 480.0 MB/s
SMART status: Not Supported

Options... Format Drive -- Safe Removal -- Benchmark
Volumes: Unknown 0.0 kB
Usage: -
Device: /dev/sdf
Partition type: -
Capacity 0.0 kB (0 Bytes)
(Option to format volume)



OKAY...
So I got all that... this is what happens when I try and format drive with the master boot record:
Error formatting drive: (Operation Failed)
Details: ```
Error creating partition table: helper exited with exit code 1: In part_create_partition_table: device_file=/dev/sdf, scheme=0
ped_device_get() failed
```If I try to Benchmark with Read-only I get: ```
Error benchmarking: helper exited with exit code 1: Error seeking to position 14693624574866735104 for /dev/sdf: Invalid argument
```And if I try to Format Volume with Ext4 (Taking Ownership with NO ENCRYPTION):
details of error: ```
Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.14 (22-Dec-2010)
mkfs.ext4: Device size reported to be zero.  Invalid partition specified, or
    partition table wasn't reread after running fdisk, due to
    a modified partition being busy and in use.  You may need to reboot
    to re-read your partition table.


 

```
Any chance of somewhat fixing this? If I could get whatever files I had on it that would be great too but just to have it usable again would be great! 16GB definitely is worth salvaging if possible :P

Big thanks to anyone who can help :P

---

### Post by tgalati4 on 2011-05-07
The act of plugging and unplugging a USB flash thumb drive can weaken and break the solder connections of the 4 vital pins.  2 pins are voltage (ground and 5VDC) and 2 pins are data (+ and - balanced digital signal).  One small crack in the solder joint of one of those pins will cause mysterious problems.

I've repaired one USB stick before.  It's not pretty, but doable with a small soldering iron and patience.

Kingston is a reputable brand, and they will probably replace it, but you probably want to recover your data.

You might consider testdisk and photorec:

sudo apt-get install testdisk
man photorec

Recover the data to a hard drive and see how much you can retrieve.  How long have you had the drive?  How many plug/unplug cycles on it?  Do you keep it on a keychain?

Also, USB sticks are formatted with FAT without a partition table.  So unless you partitioned with gparted (or similar) to create a valid partition table, you can't run any tools to repair (other than photorec).

Also, if you partition with gparted (or similar) it will create a partition table with a Cylinder, Head, Sector (CHS) count that is appropriate for hard drives, not flash drives.  You need to preserve the CHS count when formatting, otherwise BTH.

Bad Things Happen.

---

### Post by Robert1995 on 2011-05-08
Well none of the above tools work (testdisk and photorec) as when I chose which device it doesn't list my stick, only my HDD. My HDD is dev/sda1 while my USB is dev/sdf which doesn't show up anywhere other than the disk utility :(

Also Gnome Partition Editor doesn't find the device either :(

---

