---
title: "Problem with HP L1706 LCD monitor"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by odiseo77 on 2006-10-17
Hi all, I recently bought a new computer. It has an HP L1706 LCD monitor (17 inches), but I'm having problems on ubuntu with this monitor: sometimes, the screen starts to vibrate a look blurred and my Ubuntu gets frozen. It happens randomly without any apparent reason. The monitor manual says the refresh rates should be set to 60 Hz. The monitor section of my xorg.conf looks like this:

```
Section "Monitor"
        Identifier      "HP L1706"
        Option          "DPMS"
EndSection
```

As you can see it doesn't have the refresh rates set, but I read in the xorg.conf manual that, if no refresh rates are set, xorg.conf sets them to 60 Hz (the default), so it shouldn't be the problem (I think). 

The default depth on my xorg.conf is 24 and the higher resolution is 1280x1024. The monitor manual says the recommended settings are 32 bits color and a resolution of 1280x1024; I tried to change my color depth to 32 bits on xorg.conf, but I got errors when restarting the X server, so I had to change back to 24 bits. 

Also, I have an e-Geforce 6200 LE Nvidia graphic card (DDR2, 256 MB, AGP 8X) and installed the latest Nvidia drivers.

As a side note, it happenned like 3 times on my gentoo install too (but gentoo didn't get frozen).

Does anyone know which might be the problem and how to solve it??

Thanks in advance.

EDIT: Oh, I forgot to say, I'm using Ubuntu Dapper, and I already checked the monitor cable and the graphic card is properly attached to its slot.

---

### Post by juanchito2006 on 2006-12-27
Have the same problem no solution I've found to date](*,)

---

### Post by odiseo77 on 2006-12-27
> **juanchito2006 said:**
> Have the same problem no solution I've found to date](*,)

I found what I think was the problem, because since then I've not had the problem again. I'm connecting to the net through a wireless connection (my card is an edimax that works with the ralink driver, included in the ubuntu standard kernels).  Well I had both, my ethernet card and my wireless net card activated and I found it made my system unstable, so I disabled my ethernet card and everything is working fine now. Maybe if you're using two net cards and have both activated, that's what's troubling you??

Regards.

---

### Post by juanchito2006 on 2006-12-27
No, just the onboard one. I've got a HP 2200dx Microtower.

---

