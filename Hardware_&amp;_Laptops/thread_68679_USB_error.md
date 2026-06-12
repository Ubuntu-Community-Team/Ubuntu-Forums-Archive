---
title: "USB error"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by HairlessHippie on 2005-09-23
I had a video card that went bad and I had to replace it. In the meantime I configured my motherboard to go back to the onboard video, no problem. I booted into 5.04 and I get a kernal error that states

USB 1,2  device not accepting address 2, error -71



I don't know what went wrong, and Win Xp recognizes USB no problems, but my Ubuntu bootup freezes when it tries to set up hotplug. Any help is greatly appreciated.

---

### Post by HairlessHippie on 2005-09-27
Must have been a interrupt request problem, although I switched the settings on my motherboard to use the pci card for video first and the onboard video second, I actually failed  to disable the onboard video. Once I did this it musta freed up some resources as I am now able to boot into Ubuntu 5.10 now.:)

---

