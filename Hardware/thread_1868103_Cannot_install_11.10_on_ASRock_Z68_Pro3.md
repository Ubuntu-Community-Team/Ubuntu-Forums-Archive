---
title: "Cannot install 11.10 on ASRock Z68 Pro3"
date: 2011-10-23
forum: Hardware
---

### Post by zim2dive on 2011-10-23
Failing all attempts to install on this mobo (with i3-2100 and 8G ram).  I have updated to the latest BIOS (1.60)

Can start from DVD and USB.. get to the 1st pick menu.. choose to boot Ubuntu (have tried 32-bit, 64-bit, and Kubuntu 64-bit)... 

misc message scroll by.. last I see is a text about Bluetooth and then saned... then I get this screen:

Not sure what else to try??

thanks,
Mike

EDIT: had to remove my nvidia GPU and do the install running off IGP.

---

### Post by grJubei on 2011-11-26
Same here. I have installed an nVidia graphics board and disabled the onboard one from the BIOS but still cannot get past that text (I'm pretty sure we get stuck at the same point in installation but I never see that kind of screen, it remains in console mode).

---

### Post by grJubei on 2011-11-26
I tried a precise pangolin daily build and now I get this:

[IMG]http://img855.imageshack.us/img855/4327/img20111126192307.jpg[/IMG]

---

### Post by fjgaude on 2012-02-27
Have you tried booting with the internal graphics, forget the external video for the moment?

I have an ASRock Model 68M-ITX/HT, Z68 chipset, and it works fine with only one issue, will not resume.

You have to try a different driver for the Nvidia graphic board. Lots of folks have had this issue.

---

