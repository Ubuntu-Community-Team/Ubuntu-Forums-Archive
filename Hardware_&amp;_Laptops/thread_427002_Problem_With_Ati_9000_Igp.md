---
title: "Problem With Ati 9000 Igp"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by SANOSUKE_SAGARA on 2007-04-29
hello everyone...

I am new in linux... I have a problem with installing the driver. 

when i finish installing the driver and I type on the console this

# fglrxinfo
I got this

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

my question is how do I change that to this....

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)

later I typed this

# grep -i dri /var/log/Xorg.0.log | grep -vE "driver|drmOpenDevice"

and i got this 

"
        X.Org Video Driver: 1.0
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading extension XFree86-DRI
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
        Module class: X.Org XInput Driver
        Module class: X.Org XInput Driver
        Module class: X.Org XInput Driver
        Module class: XFree86 XInput Driver
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                           
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
        ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): NoDRI = NO
(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.
(==) fglrx(0): OpenGL ClientDriverName: "on_igp9x00_we_do_not_support_dri.so"
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): * DRI initialization failed!                  *
(EE) AIGLX: Screen 0 is not DRI capable
root@sanosuke:~# fglrx
bash: fglrx: orden no encontrada
root@sanosuke:~# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

i noticed that it shows this

(WW) fglrx(0): DRI is not supported on Radeon 9000/9100 IGP (RS300/RS350) hardware.

what does it mean?

I follow the instruction correctly from this website

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

and hasn't change that... could anyone can help me.... please



sanosuke

---

### Post by bonzini on 2007-04-30
I have an ATI 9000 IGP on my Toshiba.  It appears that the drivers from ATI do not support this capability on this chipset.

I have had good luck with the open-source ATI drivers that come with Ubuntu.  It's not super-speedy, but it works (glxgears fps ~ 700).

You don't say why you want to use the proprietary drivers; maybe you should reconsider?

---

