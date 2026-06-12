---
title: "Graphics has artifacts after installing kubuntu-9.04"
date: 2009-10-28
forum: Hardware
---

### Post by jerrry94087@yahoo.com on 2009-10-28
I upgraded old Toshiba laptop from Gentoo to kubuntu-9.04. Driver used for graphics is intel-i810.
After this I see various graphics artefacts: damaged letters, random lines on the screen.

Here: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
I found the discussion that the latest driver has some problems. So I followed instructions there and downgraded my driver from 2.6.3 to 2.4.1.

Now there are much fewer artefacts, they are different, but they are still there. Some icons are damaged, random lines on screen.

I also refreshed all *xorg* and *font* packages without any impact on the problem.

What could be the problem? What is the stable configuration for i810 graphics hardware?

My kernel is 2.6.28.

---

