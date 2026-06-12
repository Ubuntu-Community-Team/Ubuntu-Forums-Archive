---
title: "Radeon driver/DPI problem with Xubuntu 9.10"
date: 2009-11-02
forum: Hardware
---

### Post by mbrijun on 2009-11-02
Hello,

I have installed the new Xubuntu 9.10 on an old Dell Latitude C640 laptop. The first thing I notice is the size of the font - really small to the point it hurts my eyes.

Having done some research I came across this bug report: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/80940](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/80940)

The symptoms that I have match exactly. I do have a Radeon Mobility card and the dpi is set to 96. The real dpi should be 124 instead. I failed to find a working xorg.conf combination, having tried various suggestions including "DisplaySize", "IgnoreEDID", "noDDC" and "PanelSize".

One of the last comments in the bug report suggests forcing the xserver to accept dpi of 124. Let me cite the post: "Workaround: as karmic does not use xorg.conf in the default setup, I've modified /etc/kde4/kdm/kdmrc to start the xserver with the options -dpi 124."

What do I need to modify in order to make XFCE start with the above setting?

Best regards,
Martin

---

