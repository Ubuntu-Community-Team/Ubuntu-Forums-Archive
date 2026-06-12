---
title: "Server w/ RAID not loading GRUB on Startup"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by ddsvi78 on 2009-10-01
After a fresh install of Ubuntu Server I get the error " No bootable device -- insert disk and press any key "

If I put the live CD in and select "Boot from first hard drive" Grub loads and everything comes up as expected. But I cant seem to get the system to boot directly to the first hard drive without the Live CD. 

I have checked the boot order in the BIOS and have set the Hard drive to be first in line, this hasnt helped. Just for fun I tried going through the system recovery option on the Live CD and when it gets to detecting the filesystem. It says something to the affect of No file system found, it may not be mounted or something like that. If you need the full error I get here, I can go through that process again.

But then I put the live cd in again, select boot from first hard drive and everything boots up perfectly.

I have tried re-installing grub with:
```
find /boot/grub/stage1
(hd0,0)
(hd1,0)

root (hd0,0)
setup (hd0)

```
And get the same results

Any ideas?

---

