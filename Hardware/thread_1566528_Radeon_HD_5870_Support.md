---
title: "Radeon HD 5870 Support?"
date: 2010-09-02
forum: Hardware
---

### Post by achelis on 2010-09-02
Hi.
I'm about to buy the components for a new desktop, and it seems the Radeon HD 5870 is a good buy for my needs/desires.

But does anyone know if it works well with Ubuntu (preferably 64-bit)?
And if not, is there any similar cards that does ?

---

### Post by achelis on 2010-09-04
*bump*

Is there really noone which has tried this card ? Or similar cards ?

Basically I'm concerned because I know ATI cards used to cause a lot of problems for Ubuntu users, and secondly because hardware support for newer graphics cards can be pretty bad as well so I would rather buy a slightly older model if I knew it worked perfectly with Ubuntu :)

Hope someone can help :)

---

### Post by xircon on 2010-09-04
ATI support is not brilliant, I have a Mobility Radeon HD 5000 series, it works, but for example I get screen artifacts with cairo-dock in opengl mode.

---

### Post by achelis on 2010-09-04
Hmm, in that case I guess I'm better off getting an nVidia card - possibly something like the GTX460. Does anyone have experience with that one?

---

### Post by destine on 2010-09-07
heya,

just got this card and am not the happiest :(. 

things periodicaly get messed up. all the window borders keep going black as well as the avant-window-manager dock. 

I get some lines showing up my desktop background. 

I have to restart x to get it back to normal...

Just had a major hardware change so the install is fresh. 

Using the latest ati driver from their site which i found to be a bit clumsy to install. 

everything seems to run fine under windows so the hardware is not at fault

Found this in the messages log not sure if it has anything to do with the problem.
```

[25409.839511] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line: 63
Sep  8 02:07:24   [25423.019641] [fglrx] IRQ 63 Disabled
Sep  8 02:07:25   [25424.360128] bridge-wlan0: is a Wireless Adapter
Sep  8 02:07:28   [25426.747356] [fglrx] Firegl kernel thread PID: 21736
Sep  8 02:07:28   [25426.747525] [fglrx] IRQ 63 Enabled
Sep  8 02:07:28   [25426.992563] [fglrx] Gart USWC size:1240 M.
Sep  8 02:07:28   [25426.992565] [fglrx] Gart cacheable size:491 M.
Sep  8 02:07:28   [25426.992569] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep  8 02:07:28   [25426.992571] [fglrx] Reserved FB block: Unshared offset:f91f000, size:3e1000 
Sep  8 02:07:28   [25426.992572] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Sep  8 02:07:46   [25445.370107] bridge-wlan0: is a Wireless Adapter
Sep  8 02:37:05   [27203.619906] [fglrx] IRQ 63 Disabled
Sep  8 02:37:05   [27203.920172] bridge-wlan0: is a Wireless Adapter
Sep  8 02:37:06   [27205.211692] [fglrx] Firegl kernel thread PID: 6775
Sep  8 02:37:06   [27205.211863] [fglrx] IRQ 63 Enabled
Sep  8 02:37:06   [27205.434503] [fglrx] Gart USWC size:1240 M.
Sep  8 02:37:06   [27205.434505] [fglrx] Gart cacheable size:491 M.
Sep  8 02:37:06   [27205.434509] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep  8 02:37:06   [27205.434511] [fglrx] Reserved FB block: Unshared offset:f91f000, size:3e1000 
Sep  8 02:37:06   [27205.434512] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Sep  8 02:37:09   [27207.908027] Assertion failed in ../../../../../../../../drivers/2d/lnx/fgl/drm/kernel/hal_evergreen.c at line: 63
Sep  8 02:37:09   [27208.424296] [fglrx] IRQ 63 Disabled
Sep  8 02:37:10   [27208.646177] [fglrx] Firegl kernel thread PID: 6823
Sep  8 02:37:10   [27208.646347] [fglrx] IRQ 63 Enabled
Sep  8 02:37:10   [27208.874840] [fglrx] Gart USWC size:1240 M.
Sep  8 02:37:10   [27208.874843] [fglrx] Gart cacheable size:491 M.
Sep  8 02:37:10   [27208.874846] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Sep  8 02:37:10   [27208.874848] [fglrx] Reserved FB block: Unshared offset:f91f000, size:3e1000 
Sep  8 02:37:10   [27208.874850] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 

```Box specs:
AMD 2 x6 1090T
Gigabyte ATI HD5870 1GB
4GB DDR3 2000Mhz 
Asus Crosshair iv formula motherboard
Ubuntu 10.04.1


cheers


Seems there is no 3d support with the newest drivers, there is an issue with x11 which answer my above issue
[http://ubuntuforums.org/showthread.php?p=9745702](http://ubuntuforums.org/showthread.php?p=9745702)

---

