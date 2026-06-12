---
title: "Dapper Flight 2 works on Winbook A212"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by gregwa on 2006-01-20
I'm not sure this is actually the right place to put this post, so forgive me if it isn't.  However, that being said, Winbooks CAN run Linux.

Winbooks are a really nice, low cost laptop but provides almost NO support for Linux.  So if you want to run Linux on a Winbook, you are pretty much on your own.

I was running Debian 3.0 on my old Winbook J1 before it pretty much died.  A new motherboard was required which was around $400 plus shipping to get fixed.  They were offereing the Winbook A212 just before christmas for $700 with a $150 rebate.  Moving from a 1 gig processor with 256 meg and only 2 USB 1.0 ports to a 1.6 gig processor with 512 meg seemed like a no brainer for us.  

When I bought it, though, I ran into the old New Machine vs. Linux issue.  No support for the new hardware.  Debian 3.1 wouldn't run.  Mandriva was terrible, Suse was (if not worse) just as bad.  I stumbled across Ubuntu.  However, Breezy wouldn't run either due to the ATI Radeon express video card.  Enter Dapper.  It ran right "out of the box".  I was totally blown away.

While there have been some issues with upgrades due to X breakage, it runs just fine with only one issue, which is a simple work-around.  If you try it, make sure you check out the clock.  It will probably run at double speed (2 seconds for every one second).  The easy fix is known.  In /boot/grub/,  modify the menu.lst to include "disable_timer_pin_1" in the kernel start line.  You should also add that to the #nonaltoptions line (before 'quiet splash') so that any updates to the kernel will keep this.

Just wanted everyone to know that Winbooks CAN run linux.

Thanks all

Greg

---

### Post by joek on 2006-02-24
Hi,

KUbuntu LiveCD Dapper 4 works with my WinBook A215, however, sadly the RALink 802.11g doesnt work.

---

