---
title: "Cannot boot from USB drive"
date: 2008-12-18
forum: Hardware
---

### Post by gnomeout on 2008-12-18
**PROBLEM:** I have a 4gb usb flashdrive with a persistant ubuntu installation on it(from their website!). this boots fine on my computer at home(as long as i unplug my external HD). but I cant seem to make it work on this computer.

**BACKGROUND:** I have changed the BIOS and made sure everything is in order for it to check the usb for boot. but it still does not. interestingly, i tried to disable booting from the internal HD. and when i did it STILL booted the HD. and when i went back to the BIOS setup it was still disabled on the boot priority list!!!(thats not my issue, but perhaps it can provide some insight?)

Also, i thought a BIOS upgrade might help, but i cant determine the manufacturer of the mobo, and emachines(made the computer) says it does not need an upgrade(i was asking for the mobo manufacturer though, which they never told me, do they make their own?), but they were also in the middle of shrugging me off since the warranty has expired. I also tried each usb port in case the boot was wedded to just one. I am seriously perplexed!

here is the computer i am working on: 
[http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T3256](http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T%20Series&model=T3256)

(click on "specifications" to see them)

its moderately urgent since I am only here for a couple weeks anyway, but if i have to spend another day on windows i might kill myself.

please and thanks!!

---

### Post by nixscripter on 2008-12-18
The only thing I can suggest is to tinker with BIOS settings which affect USB, such as:

1. Legacy USB keyboard support (which changes assumptions about various devices at boot)
2. Enabling USB (you may laugh, but it took me an hour to figure this out one day)
3. Plug-and-play OS (might prevent checking USB at all until after boot)
4. If there is a separte setting to disable different USB ports, e.g. front vs. back of the machine
5. USB 1.0 vs. 2.0 support (is the flash drive 1.0 or 2.0, by the way?)

Experience has taught me BIOSes are always stupid and quirky, no matter how many featuers they have, or how smart they first appear.

---

