---
title: "Hardware Drivers download hung"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by InquiringMind on 2009-11-03
When 9.10 came out, I downloaded and installed the 32-bit version on an HP HDX18 laptop, including the proprietary "NVIDIA accelerated graphics driver (version 185)" using System/Administration/Hardware Drivers.  Then I noticed that all the memory wasn't recognized and I needed a 64-bit version, so I downloaded and installed that, completely replacing the 32-bit version  (ubuntu.com doesn't make it easy to get the 64-bit version, but that's another topic).  Everything seemed ok, except that when I tried to install the NVIDIA driver the same way, the download stopped about a quarter way through.  Thirty or so hours later, the download progress bar hadn't changed.  There were no signs of communication problems on my end, so I figured the server had died.  Cancel did not respond, so I have rebooted and retried several times since then.  The progress bar still shows a one-quarter finished download and there is no sign of any further transfer on System Monitor.  I thought something must have got tangled up on my end, and left the problem for later.
 
Then, today, I installed the 32-bit version on an HP2133 netbook.  Again, everything seems to be ok, but when I tried to use Hardware Drivers to install the Broadcom B43 wireless driver (over a wired connection which works fine for everything else), it showed no signs of starting to download.  The progress bar shows nothing after over six hours.
 
One success in three tries; two different machines, two different drivers, no sign, so far, of other problems.  I have since successfully downloaded and installed other software on the HDX18 using Ubuntu Software Center, and Firefox, at least, works just fine on the HP2133 while the Hardware Drivers download progress bar just sits there showing nothing happening.
 
What's going on with the Hardware Drivers download?  Is anyone else having this problem?

---

### Post by sleepysandman on 2009-11-05
I had the exact same problem.  The hardware dialog completely freezes up in 9.10 when I try to download various drivers, like a wireless driver or Nvidia drivers.  It sometimes freezes when just looking for drivers before the dialog has even come up.  I finally was able to fully download one of them after about a dozen tries, doing nothing different.

---

### Post by fabecool on 2009-12-13
Hi there!

I'm having the same problem with the NVidia driver and with my wireless card driver (broadcom B43). The cancel button does not work and there is no way to close the Hardware Drivers window.

I read in other posts that some people ran into similar issues with the Hardware Drivers application, and they finally got it to work after several reboots.

Did you guys (or s.o. else) get it solved?

Thanks, and good luck to others who run into the same problem!

---

