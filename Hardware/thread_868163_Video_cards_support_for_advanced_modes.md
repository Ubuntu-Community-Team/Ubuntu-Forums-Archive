---
title: "Video cards support for advanced modes"
date: 2008-07-23
forum: Hardware
---

### Post by josephmo on 2008-07-23
I have an ATI Radeon HD 3600 card and a Ubuntu 8.04 installation. The built-in driver does not support the full resolution of my video card, nor does it allow for advanced graphics mode.

I went to the ATI site, but it seems as if the 3600 is not supported by their proprietary driver (but the ATI site is not helpful at all on what cards are supported). Does anyone know which ATI chipsets are supported by the proprietary ATI drivers? How about Nvidia Chipsets?

---

### Post by markbuntu on 2008-07-23
The entire HD3600 series is supported by ATI. MY HD 3650 works great.

The directions here, which are the only ones that I know for sure to work, have not been updated yet for the 8.7 driver but you can get the 8.6 driver from ATI by following some links from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

The directions for installing 8.6 are here, use method 2, if the site has been updated for 8.7, get that driver instead. Follow the directions very carefully, especially if you are using amd64:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)


Release Notes for 8.6

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

Personally, I am going to wait until the directions above have been updated before I install 8.7, the changes are very insignficant compared to the changes between 8.4 which is in the repos and 8.6  Other directions I have tried in the past have led to nothing but disaster.

Envy will install the 8.4 driver which has problems that are fixed with 8.6.

---

### Post by josephmo on 2008-07-23
> **markbuntu said:**
> The entire HD3600 series is supported by ATI. MY HD 3650 works great
Does your card work in all modes? (1680x1050 more specifically)

---

### Post by markbuntu on 2008-07-24
It works in 1920x1200, that is the resolution of my monitor and 1280x1024 because that is the resolution of my second monitor. I run them together as a big desktop. 

My 1st monitor does do 1680x1050 and 1600x1200 also but maximum in VESA mode is 1024x768.

VESA is a default video mode that provides basic functional video support without using any special drivers.

If you want 1680x1050, you need the restricted driver.

---

