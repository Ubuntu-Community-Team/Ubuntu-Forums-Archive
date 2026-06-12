---
title: "Computer Shuts Down Without Warning"
date: 2014-01-01
forum: Hardware
---

### Post by mlbailey on 2014-01-01
I have been trying to use Ubuntu, Linux Mint, Pear OS 8, etc., but after a while of usage my computer shuts down without warning.  It seems that it's overheating when I use Linux, and my motherboard is set to shut down at a certain temperature.  I'm running an AMD A10-5700 Quad-Core APU with Radeon HD Graphics.  I assumed it was because I needed to install the proprietary AMD video card drivers for my APU, but that causes my computer to reboot into a black screen, which renders my computer useless and hasn't helped the overheating issue so far.

Anyone know why Linux is causing my computer to overheat and shutdown?  Please help!  :confused:

---

### Post by bcschmerker on 2014-01-01
What fansink is on your processor?  The Advanced Micro Devices® A-Series processors have different maximum safe temperatures by model and flavor.  According to /Pages/DesktopAPUDetail.aspx at Products.AMD.com, the A10-5700 (Socket FM2, AMD® P/N AD5700OKA44HJ) dissipates 65 W and can safely run up to 71.3 °C.  Also, proper pre-treatment of the fansink is critical to safe operation, as flatness, surface finish, and type and thickness of thermal conductant are factors.

On my own AMD® Athlon 64® X2 5600+/780G chipset-based custom-build in a modified Everex® TC2502 case, I have tested several fansinks on the '64 X2 and had no significant problems to date; of course I had retrofitted a 120mm intake filter and duct to ensure that the CPU fansink gets clean air (not every user has this option).  This machine currently packs a Zalman® CNPS7800.

---

