---
title: "Troubleshooting disk errors"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by cdpuk on 2008-02-20
Last year I built a media center box for a MythTV installation, it worked perfectly for the first couple of months until one day it randomly locked up.  Thinking nothing of it at the time I just rebooted the box  only to find that since then it only achieves 5-7 days uptime before the same thing happens.

When this happens the GUI locks up and the disk activity light gets fixed on, but thankfully I'm usually able to ssh in to find out what's going on.  

Unfortunately I've not got a copy of the normal errors I see when this happens. However, a couple of weeks ago I reseated the SATA cable and took off part of the case to rule out overheating and now I'm seeing different errors:

```

[494673.371506] EXT3-fs error (device sda1): ext3_free_blocks_sb: bit already cleared for block 2732093
[494673.371520] Aborting journal on device sda1.
[494673.371788] ext3_abort called.
[494673.371793] EXT3-fs error (device sda1): ext3_journal_start_sb: Detected aborted journal
[494673.371798] Remounting filesystem read-only
[494673.372244] Remounting filesystem read-only
[494673.373030] EXT3-fs error (device sda1) in ext3_free_blocks_sb: Journal has aborted
... last message repeated lots

```

I've run short and extended SMART tests on the disk with no errors found.  Has anybody seen anything similar?  And what could be causing this - disk, motherboard, RAM?  And of course, why did this start happening after two months of perfect operation?

Thanks
-Chris

<update>

This time, when the system rebooted the automatic fsck failed - had to go through manually fixing loads of errors.  Restarting after that gave me a kernel panic, and finally restarting again seemed to work.  Things seem to be getting worse :(

---

### Post by samborambo on 2008-05-09
Have a look through your dmesg output. If you're getting some buffer I/O errors then your hard drive might be a bad egg. MythTV can really thrash your drives.

Did you get your Realtek NIC negotiation problem resolved? I'm having the exact same problem on a feisty build ( my MythTV box). Have you upgraded to Gutsy or Hardy? Thinking it may have been fixed in later kernels.

Send me a PM if you can.

Sam.

---

### Post by samborambo on 2008-05-09
Just had a thought...

Make sure your TV recordings are on a separate filesystem to the rest of your system. I've had my MythTV backend lock up hard a few times before - requiring a hard reset. After a reboot, my TV drive is corrupted and requires a manual fsck to fix. 

You should have separate partitions for slash, videos (if you have lots) and tv recordings. I use JFS for my TV partition as it has the fastest filesystem for deletion of large files. A sympton of slow deletes can be live TV throwing a hissy fit at the end of a program and it needs to auto-expire some stuff for the next program.

If it's a serious mythtv set up, use a RAID 5 array for the best performance and data integrity.

Sam.

---

