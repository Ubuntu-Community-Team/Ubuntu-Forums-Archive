---
title: "xserver-xgl possibly disabling proprietary ATI driver?"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by Hawk55 on 2007-12-08
I have an ATI Radeon X300 video card in my Dell Inspiron 9300 laptop.

When I first installed Ubuntu 7.10, and was therefore using the open source ATI driver, it seemed like the 2D rendering wasn't very fast.  Specifically, if I tried to scroll from inside a maximized Firefox or OpenOffice window, the page would scroll noticeably slowly.  Also, when I tried to click and drag the pointer across my desktop, the translucent selection window would draw slowly.

Installing the proprietary ATI driver fixed these performance issues.  However, I couldn't enable any of the compiz visual effects.  I read that this was a known issue, and that installing the xserver-xgl package would allow the effects to be enabled.

Installing the xserver-xgl package did allow the visual effects to be enabled, and Ubuntu is still reporting that the proprietary ATI driver is in use, however I'm now experiencing the exact same issues as when I was using the open source ATI drivers.

Is it possible that the xserver-xgl package is somehow forcing the use of the open source ATI driver?

---

### Post by Hawk55 on 2007-12-09
bump

---

