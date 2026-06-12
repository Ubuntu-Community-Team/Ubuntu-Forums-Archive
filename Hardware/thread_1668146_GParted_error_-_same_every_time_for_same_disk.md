---
title: "GParted error - same every time for same disk???"
date: 2011-01-15
forum: Hardware
---

### Post by Moozillaaa on 2011-01-15
Every time I do a GP task, on the same disk, and GParted re-scans after the task, I get an error message:
> 
The Kernel was unable to re-read the partition table on /dev/sd***X*** (device or resource busy). Changes made may not be reflected until after the next re-boot.

I googled, but didn't find anything that I was looking for (failing hard disk, which I think I have) (backups done - keep on topic please).

I did find one interesting search result - mentioning cylinder boundaries. This is maybe pertinent, because this disk came from a satellite DVR, which had Linux formatting, and all 3 partitions do **NOT** begin or end on cylinder boundaries!!!

SO...

When I put this disk into the computer, I deleted only the 1st 2 partitions, and kept the 3rd partition, again, which began and ended off of cylinder boundaries. Mean anything?

Any ideas here on this GParted error? Thanks...

---

