---
title: "acer aspire 5536G : acerfand and bios"
date: 2011-01-19
forum: Hardware
---

### Post by _paul_g on 2011-01-19
I am running Ubuntu 10.10 on an acer aspire 5536g.

There is no means of controlling the fan which runs constantly and loudly. 

There is a fix for the aspire one with the acerfand script which is described here :
[https://help.ubuntu.com/community/AspireOne/110L?action=show&redirect=AspireOne110L#Fan%20Control](https://help.ubuntu.com/community/AspireOne/110L?action=show&redirect=AspireOne110L#Fan%20Control)

The acerfand script supports a number of bio versions. The highest is "v0.3309".
The bios on this machine are v.1.03.

At the above link is says the following :
> 
If you upgrade to BIOS version 3310, the current  version of acerfand (v 0.7 at time of writing) throws an unsupported  BIOS error. Since the fan control is not changed by this BIOS update,  change the acerfand script like so: 
BIOS_VERSION_3109="v0.3109"
BIOS_VERSION_3114="v0.3114"
BIOS_VERSION_3304="v0.3304"
BIOS_VERSION_3305="v0.3305"
BIOS_VERSION_3309="v0.3309"
#add 3310 BIOS support
BIOS_VERSION_3310="v0.3310"Does this mean that I could simply do the same for my version of the bios?

Is there any risk in trying?

---

