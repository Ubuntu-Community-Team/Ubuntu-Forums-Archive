---
title: "Twinview maximizes windows across both monitors"
date: 2008-10-13
forum: Hardware
---

### Post by ZManODS on 2008-10-13
I am running a Dell Inspiron 9300 with a GeForce 6800 video card on Ubuntu 8.04.

Both my devices are DFP's with a resolution of 1920x1200

```

Using NV-CONTROL extension 1.14 on :0.0
Connected Display Devices:
  DFP-0 (0x00010000): Sharp
  DFP-1 (0x00020000): DELL E248WFP

```

My laptop monitor DFP-0 is on the left.

If I configure the setup in with xrandr or I configure it with nvidia-settings I always get the undesired behavior of the toolbar and windows stretching across both screens. However if I save my xorg.conf with the twinview setup and restart my computer it will load correctly, ie maximized windows will be across only one screen as well as the toolbar. 

Have any clue to what can be causing this?

---

