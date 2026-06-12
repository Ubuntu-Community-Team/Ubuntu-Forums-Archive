---
title: "Disk check/ Kernel Bug edgy"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by benhall on 2006-10-20
Recently updated to edgy from dapper, with some minor issues which I have been able to find solutions to. However, the boot process is very slow, and doesn't always complete. It seems that this is in part related to whether I use recovery mode or not (if I do, I seem to be more likely to get to X). What happens is that it gets to checking the root filesystem, frequently finds that
> /dev/sda5: Superblock last write time is in the future. FIXED.
It then does nothing. The most recent time I attempted it  in recovery mode it performed fsck and then printed
> 
/dev/sda5: Superblock last write time is in the future. FIXED.
/dev/sda5 has been mounted 30 times without being checked, check forced.
[17179601.500000] BUG soft lockup detected on CPU#0!       / 20.0%
/dev/sda5: |==============                                 \ 50.6%

It hangs at this point. My laptop is a core duo acer aspire 5652WLMi, 1.5GB memory, dual booting with XP. Any solutions/advice would be very welcome!
Thanks
Ben

---

