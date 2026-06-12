---
title: "Lenovo T61 with Intel X3100 display issues on Intrepid"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by PEugenis on 2009-01-11
My daughter's Lenovo T61 with the Intel X3100 graphics was working just fine under 64-bit Hardy (8.04), but she was finding that some of the tools that she wanted did not work well or were not supported under 64-bit.  I wiped her previous disk image and installed Intrepid (8.10) 32-bit, but now her 14.1 widescreen laptop display and external 19" widescreen displays are only recognized as supporting 1024x768.  They should both support 1440x900 (at least they did before the upgrade).

Does anybody out there have any ideas regarding how to resolve this issue?

---

### Post by PEugenis on 2009-01-16
Additional information:  When I boot with the 8.10 liveCD, it guesses the resolution incorrectly ( 1024x768 ), but when I boot with the 8.04 liveCD, it guesses the resolution correctly ( 1440x900 ).  So this appears to be specific to Intrepid.  

Does anybody out there have a suggestion?  I will give this a few more days...then will fall back to Hardy.

---

### Post by tommcd on 2009-01-17
Try following this how to:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
To run the command open a terminal (applications > accessories > terminal) and run the commands. Using a external display along with the laptop's display may complicate things. If you have problems try disconnecting the external display and then try again.

And welcome to the Ubuntu forums!

---

