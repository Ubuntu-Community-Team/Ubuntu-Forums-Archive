---
title: "Serial Mouse Problem (Solution)"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by Milton on 2005-11-25
I had my serial mouse working correctly in Hoary which I was able to do using the information on the wiki.

However when I tried the same methods on my upgrade to Breezy my xserver would fail.

The trick was that /dev/ttys0 had been renamed to /dev/ttyS0 (note the capital S). The dpkg-reconfigure method didn't seem to figure that out.

It would be very nice if serial mice could be properly detected in the future.

---

