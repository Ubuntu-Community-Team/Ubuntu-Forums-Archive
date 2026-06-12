---
title: "Check disks for faults"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by Robert Leithe on 2007-03-05
I have an external disk I suspect is faulty, or on its way to becoming so.
Right out of the blue I received a write-error when unzipping a file. I rebooted my laptop (and powered down/up the external disk), but the result is the same. I cannot access the folders on the disk anymore. And a small icon with a lock on it on the folders at "root level" (a little Windows talk there...).

I am currently reformatting the disk, and would like to check it for faults. Can someone recommend a tool for this? Basically I don't trust the disk anymore, and is likely to just throw it away and buy a new. But still. I could find *some* use for it I guess, if I only could diagnose it and know at which level it can be trusted.

Sincerely
Robert Leithe

---

### Post by colo on 2007-03-05
You want to test your disk using `badblocks`. Should be installed by default, is manpage explains all you've got to know. Tip: be sure to use an extra-verbose mode (`badblocks -vvv`) to get an idea of how far your tests have already progressed.

Good luck ;)

---

### Post by Robert Leithe on 2007-03-05
I can't seem to get badblocks to work... Here's my results:

[B]robert@C-3PO:~$ badblocks -vvv /media/usbdisk
badblocks: invalid blocks range: 0-0
robert@C-3PO:~$ [/B]

As far as I can see using "man badblocks" the parameters for [last_block] and [start_block] are optional and defaults to respectively the last and first block on the disk.

The disk is newly formatted to ext3 and is currently mounted.

---

### Post by colo on 2007-03-05
Yeah well, that's intended behavior :)
badblocks does not test filesystems (that's fsck's job). badblocks is only suitable for testing the physical characteristics of block devices, and cries out loud if it finds those faulty.

It is also unnecessary to make sure those block-devices don't contain any mounted filesystems, and there should not be any other process running accessing them.


So, say your disk is represented by the device node file /dev/sda, you'd run `badblocks -vvv /dev/sda`. You may want to increase the number of blocks tested at once, as this is able to greatly improve the speed of the process, while still yielding accurate results.

---

