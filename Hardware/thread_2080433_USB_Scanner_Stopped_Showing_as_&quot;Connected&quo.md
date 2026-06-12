---
title: "USB Scanner Stopped Showing as &quot;Connected&quot;"
date: 2012-11-04
forum: Hardware
---

### Post by KutWrite on 2012-11-04
I posted this under someone else's thread, but noticed it said "SOLVED," so I'm reposting as my own thread:

Just the USB scanner has become a problem.  I have a Toshiba Satellite A650 laptop (Intel I5) and a 5-outlet USB hub.  All are working fine.

All connected devices worked fine in  Natty, 11.04.   Last month (Oct '12) I upgraded to Oneiric 11.10 and  after some diddling, got everything going.  I've been doing updates  weekly.

A week ago, the printer stopped being "seen."  I reinstalled CUPS and  the HP driver and now have two drivers, but one works and I'm stickin'  with that.

I've changed nothing else except updates. All was OK until a few days ago.  The Scanner stopped being seen as "connected."

I normally use Simple Scan.   I tried XSANE, same problem. 

lsusb does see the scanner:

Bus 003 Device 004: 
ID 04b8:0118 Seiko Epson Corp. Perfection 4180 (GF-F600)
  
the driver was working with 11.04 and 11.10.

I tried warming up the scanner, then unplugging and replugging the USB as per another post.  No change.  I also checked the kernel:  It's   3.0.0-26-generic-pae.

I rebooted multiple times.  No change. I tried uninstalling and reinstalling Simple Scan. No change.

The laptop is dual boot, and Windows 7 operates the scanner through the same USB hub etc.

I'd appreciate all ideas and suggestions!

Dan

---

