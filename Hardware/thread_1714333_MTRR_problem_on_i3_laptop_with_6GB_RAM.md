---
title: "MTRR problem on i3 laptop with 6GB RAM"
date: 2011-03-25
forum: Hardware
---

### Post by npallett on 2011-03-25
I'm running Ubuntu 10.10 (maverick) 64Bit on an MSI Intel i3 Core laptop with 6GB ram.

I get the following error message in /var/log/dmesg;

[   26.756339] [drm] MTRR allocation failed.  Graphics performance may suffer.

Also, I get very choppy playback when playing DVDs.

I get the following output from "cat /proc/mtrr":

cat /proc/mtrr 
reg00: base=0x000000000 (    0MB), size= 8192MB, count=1: write-back
reg01: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg02: base=0x0dc000000 ( 3520MB), size=   64MB, count=1: uncachable
reg03: base=0x1c0000000 ( 7168MB), size= 1024MB, count=1: uncachable
reg04: base=0x1a0000000 ( 6656MB), size=  512MB, count=1: uncachable
reg05: base=0x19c000000 ( 6592MB), size=   64MB, count=1: uncachable
reg06: base=0x17c000000 ( 6080MB), size=   64MB, count=1: uncachable


If I run "mtrr-uncover" as recommended in other posts to the forum, I get the following:


# /usr/src/mtrr-uncover-2009august14/mtrr-uncover 
Initial MTRR configuration:
 0  0x000000000-0x1ffffffff write-back
         2  0x0dc000000-0x0dfffffff uncachable
         1  0x0e0000000-0x0ffffffff uncachable
         6  0x17c000000-0x17fffffff uncachable
         5  0x19c000000-0x19fffffff uncachable
         4  0x1a0000000-0x1bfffffff uncachable
         3  0x1c0000000-0x1ffffffff uncachable
/usr/src/mtrr-uncover-2009august14/mtrr-uncover: 10 MTRRs needed but only 8 in architecture.


Does anyone have any suggestions as to how I properly configure mtrrs for my hardware ?

---

