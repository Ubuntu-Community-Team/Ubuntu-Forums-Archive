---
title: "External monitor on laptop doesn't display 1920x1080"
date: 2010-05-23
forum: Hardware
---

### Post by wraitbone on 2010-05-23
Hooking my Asus F6V laptop on my Acer V223HQ external monitor doens't give me the option of adjusting my screen resolution for that monitor to 1920x1080, while I know the monitor is capable of this.

Does anyone have some tips or tricks?

Using:
Ubuntu 10.04 64-bit, gnome desktop (2.30.0)
ATI/AMD proprietary driver FGLRX graphics driver
ATI Technologies Inc Mobility Radeon HD 3400 Series
Linux kernel 2.6.32-22-generic

System testing returns this message for "This display is using the following resolution:
unknown (impossible to determine resolution with fglrx)"

---

### Post by dino99 on 2010-05-23
[http://www.amd.com/us/products/notebook/graphics/ati-mobility-hd-3000/hd-3400/Pages/hd-3400-specs.aspx](http://www.amd.com/us/products/notebook/graphics/ati-mobility-hd-3000/hd-3400/Pages/hd-3400-specs.aspx)

.....  

Secondary supports 18-, 24-, and 30-bit digital displays at all resolutions up to 1920x1200 ([COLOR="Blue"]single-link DVI only[/COLOR])1 or 2560x1600 (dual-link DVI)1

add this ppa:  [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by wraitbone on 2010-05-25
Solution for me:

I used Ubuntu Tweak to enable the "X updates" PPA. 

This gave an update and after I restarted my system I got the option in ATI Catalyst to select the resution of 1920x1080 for my external monitor.

It might be the PPA described in the previous post but then achieved in the "no experience with linux/terminal/repositories" way. :P

Thank you for the suggestion, this really helped in finding the right solution.

Thanks!

---

