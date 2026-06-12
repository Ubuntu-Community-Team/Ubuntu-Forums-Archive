---
title: "Unable to read CD"
date: 2010-06-15
forum: Hardware
---

### Post by JKyleOKC on 2010-06-15
Attempting to install a commercial package into a Win2K VM, I put its CD into the drive and waited for the autorun setup code to go into action. Instead, I got an error message from my Hardy Heron host that it was unable to mount the disk! The message listed a number of possible causes and suggested that I check the syslog for more details. Here's the tail end of a page or so of syslogged errors:

```
Jun 15 13:55:16 mehitabel kernel: [1041976.891174] attempt to access beyond end of device
Jun 15 13:55:16 mehitabel kernel: [1041976.891177] sr0: rw=0, want=68, limit=4
Jun 15 13:55:16 mehitabel kernel: [1041976.891428] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
Jun 15 13:56:53 mehitabel kernel: [1042074.038506] cdrom: This disc doesn't have any tracks I recognize!
```

I then put the disk into my laptop that dual-boots Hardy and WinXP Pro, and XP had no trouble at all reading it and getting the data I needed to transfer into the Win2K VM (license information for the program).

It's possible that the software publisher may have deliberately done something to copy-protect the disk, that makes it unreadable by Linux but perfectly okay for Windows system. However I'd like to know whether it was that, or something else, that made it unreadable! Anyone have any ideas?

---

