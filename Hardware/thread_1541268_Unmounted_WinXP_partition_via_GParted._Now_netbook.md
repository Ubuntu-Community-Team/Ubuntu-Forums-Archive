---
title: "Unmounted WinXP partition via GParted. Now netbook can't boot from HDD or USB."
date: 2010-07-28
forum: Hardware
---

### Post by Rental Car Cowboy on 2010-07-28
Hey,

First, I really tried to search the forum for this but seems as though I could only find people with half my problem.

My Toshiba NB205 netbook came with WinXP, but I squished Ubuntu Remix into some remaining space and it worked beautifully.

Today, in an effort to resize my NTFS WinXP partition, I saw that I could only resize unmounted partitions. Unaware of what "unmount" means, I clicked my WinXP partition and unmounted it. A yellow triangle appeared next to the partition. (I never even got to fiddle with any resizing at this point)

After restarting the netbook, it tries to boot from the harddrive and immediately displays:

[INDENT]error: unknown filesystem.
grub rescue>[/INDENT]

with a blank line waiting for input. While command "help" just returns "Unknown command", "ls" returns (hd0) (hd0,5) (hd0,3) (hd0,2) (hd0,1).

When I tried to boot Ubuntu Remix and then GParted from USB (same USB stick I used for the install), both attempts bring me to a screen that displays:

[INDENT]Operating system not found
...
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.[/INDENT]

**So, in as few words as possible:**

I unmounted my Windows XP partition from GParted from within my Ubuntu Netbook Remix partition and can't boot from HDD/USB at all.

---

