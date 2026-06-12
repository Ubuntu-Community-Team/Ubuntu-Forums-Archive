---
title: "usa19hs !?"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by mmdski on 2007-10-25
I just bought a brand new shiny usb to serial converter that I've heard a lot of hype about, but it doesn't seem to be supported in Gusty. Said converter is the Keyspan USA19HS. I've noticed other 'usa19' drivers, but I don't see the 'hs'. Is there a way for me to make this work without recompiling the kernel? If not, can someone recommend another hyped up one that works? 

The main reason that I'm getting it is to program AVRs. I tried to upload text to a Butterfly and it got all screwed up. I was using a dongle that used the pl2303 driver.

---

### Post by blakesle on 2007-10-26
I have found the solution to the Keyspan problem.

Go to this site and follow the instructions. Very simple and quick.

Only thing he did not tell you it to re-boot your system after loading the driver.

[http://www.denis.lemire.name/2007/10/19/ubuntu-keyspan/](http://www.denis.lemire.name/2007/10/19/ubuntu-keyspan/)
__________________

---

### Post by mmdski on 2007-10-26
Yeah... I tried that. Wrong architecture. I installed the amd64 version. I'm not sure how to build a deb package, otherwise I'd do it myself. Maybe someday I'll read up on it.

---

### Post by mmdski on 2007-10-26
Well... apparently the 2.6.22-14 kernel doesn't have the driver, but the 2.6.22-15 and 2.6.22-16 kernels do. So it works now! Can anyone explain why there are three kernels now? or did something get screwed up with my upgrade?

---

