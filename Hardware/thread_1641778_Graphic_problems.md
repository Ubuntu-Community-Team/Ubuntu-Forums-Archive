---
title: "Graphic problems"
date: 2010-12-09
forum: Hardware
---

### Post by Dsky on 2010-12-09
i've a Toshiba M40-282, with an ati mobility x700.

i know about the problems with ati x700.. the system is using open source driver.. in fact I tried with a lot of releases and even Fedora  the glxgears comand but unsuccesfully.

I was using ubuntu 9.10 and with "normal" visual effect was all right (apart 3d or flash player)..

i updated to 10.04 and the system is totally slow.. i've to set to "none" the visual effects to make it go... 

(i tried installing the 10.10 too but it doesn't even start... i see only a black screen after the boot...)

why this happen?

with 9.10

```
 **lspci | grep -i vga**
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

**dpkg -l | grep fglrx**
ii  fglrx-modaliases                     _2:8.660-0ubuntu4.1_                         Identifiers supported by the ATI graphics dr

** glxinfo | grep render**
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV410 5653) 20090101 x86/MMX/SSE2 TCL


```

with 10.04 

```
dpkg -l | grep fglrx
ii  fglrx-modaliases                     _2:8.723.1_-0ubuntu5                              Identifiers supported by the ATI graphics dr


 glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 (RV410 5653) 20090101 x86/MMX/SSE2 TCL _DRI2_

```

differences are underlined

---

