---
title: "ATI driver"
date: 2010-06-24
forum: Hardware
---

### Post by Argonisius on 2010-06-24
Hi, I installed driver for ati graphic card (4500 series). When I switch fastly between desktops (3D cube) or I watch videos with action scenes, I can see horizontal stripes on display. Do you have an idea how to make it right? With Ubuntu open drives all works fine, but games are lagging.

---

### Post by khelben1979 on 2010-06-24
What version of the ATi driver do you have installed? Also, give us hardware output by typing: ```
lspci
``` from a command prompt or X shell.

---

### Post by cbrunhaver on 2010-06-24
It is called tearing.  When vertical sync to refresh (aka. v-sync or sync to vblank) isn't enabled, partially drawn frames are displayed on the screen, resulting in the vertical lines you are seeing.

You need to run the ATI FGLRX drivers (under hardware drivers and enable vsync in Catalyst Control Center.  Also install the compiz config settings manager and enable vsync under the general -> display tab.

---

### Post by Argonisius on 2010-06-24
HI, 
I enabled it in CCC and it's better, but not good. I didn't find it in compiz config manager - there's only something like "synchronize during VBlank", but bo vsync.

HW Info:
VGA compatible controller: ATI Technologies Inc M93 [Mobility Radeon HD 4500 Series]

Driver: Package version: 8.723.1-100408a-098580C-ATI
        2D driver version: 8.72.11

Thanks for help.

---

### Post by cbrunhaver on 2010-06-24
Yes, that is the setting in compiz.

You will probably need to disable desktop effects (compiz) to eliminate tearing in video clips totally (and use the gl render in mplayer etc.).

---

### Post by Argonisius on 2010-06-24
Ok.

---

