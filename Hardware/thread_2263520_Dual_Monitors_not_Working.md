---
title: "Dual Monitors not Working"
date: 2015-02-01
forum: Hardware
---

### Post by andrew193 on 2015-02-01
Hello,
I've got a bit of a unique situation, whereas I am using my graphics card to power my main monitor, and my integrated graphics to power second.  Ubuntu is not recognizing this second monitor in the display options, even if I hit "Detect Displays".  Does anybody know a solution?  Also, using the integrated is enabled in BIOS.
Also, I have to use nomodeset instead of quiet-splash in boot since Ubuntu really does not like my graphics card. 

Thanks in advance,
Andrew

Specs:
Intel i5-4670K with 4600 integrated graphics outputting to second monitor with VGA. 
AMD 7870 XT outptting to main monitor over DVI
Ubuntu 14.10

---

### Post by magpie03 on 2015-02-02
Andrew,
Search on this forum and on the internet to install the proper driver for your card. Detect Displays will not work unless the proper driver is installed. Mobo's are all different and some will disable the internal video when an external card is installed reguardless of the bios setting. Your video card should support two monitors with the proper driver. You may have to get an adapter to plug into VGA into one of the other ports on your card. Using nomodeset and quiet-splash means that the proper video driver is not installed and Ubuntu is using a very basic driver to display some graphics or at least a terminal screen. 
Hope this helps...
magpie....

---

