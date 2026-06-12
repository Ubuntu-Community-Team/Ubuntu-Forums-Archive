---
title: "HIS ATI Radeon HD 4670 IceQ AGP 8x 1GB - Can't get graphics hardware acceleration!"
date: 2013-03-28
forum: Hardware
---

### Post by graphicscard on 2013-03-28
Hello, I've tried to get graphics hardware acceleration with my HIS ATI Radeon HD 4670 IceQ AGP 8x 1GB in Ubuntu, but I haven't had any luck.  

I just want graphics hardware acceleration with this card in ANY version/distro of Linux.


Can anyone help me out?

Thanks!

---

### Post by typhoon_tip on 2013-03-29
Have you installed Radeon ATI drivers from AMD ?

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

The above is for Precise, but if you go to main page, you can find guide for all versions of Ubuntu.

Good luck !

---

### Post by Mark Phelps on 2013-03-29
Didn't catch what version of Ubuntu you're using,  but if its 12.10. there are no restricted drivers that will work with that card.  AMD dropped restricted driver support for the HD 2x/3x/4x series cards last summer, so they did not update the drivers to work with the newer X-server version in Ubuntu 12.10. You are stuck with the open-source Radeon drivers for Ubuntu 12.10 and newer.

---

### Post by Yellow Pasque on 2013-03-29
> Hello, I've tried to get graphics hardware acceleration with my HIS ATI Radeon HD 4670 IceQ AGP 8x 1GB in Ubuntu, but I haven't had any luck. 
It should work out of the box. How do you know you don't have acceleration?

As for fglrx/Catalyst driver, I would avoid that completely since I've only seen negative reports of recent versions actually working with RadeonHD 4000 AGP cards.

---

