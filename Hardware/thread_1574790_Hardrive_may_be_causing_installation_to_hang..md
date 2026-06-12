---
title: "Hardrive may be causing installation to hang."
date: 2010-09-14
forum: Hardware
---

### Post by josephshanak on 2010-09-14
I recently powered off my laptop when it froze while running some application in Windows 7. When I turned it back on it wouldn't boot, and to top it off it wouldn't even go to the bootloader (grub2). It just said "No bootable Disc found" or something of the sort.

Now I'm trying to reinstall ubuntu (1. So I can install grub again, and 2. because I hadn't used my 9.10 partition yet so I might as well install 10.04), but it hangs 5% through the install, which is where it was formatting part of the drive I think.

When I jumped to the terminal I kept on getting errors, something like "FPDMA failed". So later when I booted up to the CD I tried using smartctl to figure out if there was a problem. I don't know how to interpret the info though.

This was the most recent error that sudo smartctl -a /dev/sda showed up with:
```

Error 6530 occurred at disk power-on lifetime: 1012 hours (42 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 00 00 00 00

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 00 00 00 40 00      01:38:11.056  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      01:38:11.055  SET FEATURES [Reserved for Serial ATA]
  ec 00 00 00 00 00 a0 00      01:38:11.054  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      01:38:11.053  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 00      01:38:11.053  SET FEATURES [Reserved for Serial ATA]


```

It's bad enough that I messed up my windows partition, but now I can't even boot into linux or reinstall it.

---

### Post by josephshanak on 2010-09-15
Ok. It's definitely the hard drive. I let it sit hanging overnight and it came up with an error saying it failed to create the ext4 partition.

---

### Post by josephshanak on 2010-09-15
and I can't even zero-fill the drive.

[CODE
]ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000722272 s, 0.0 kB/s
[/CODE]

---

