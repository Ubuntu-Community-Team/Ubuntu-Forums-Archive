---
title: "graphic problem after ubuntu upgrade to 15.10"
date: 2015-10-29
forum: Hardware
---

### Post by mahdird5 on 2015-10-29
I did an upgrade to my ubuntu from 15.04 to 15.10 but after this  upgrade I got a graphic problem, sometimes the characters/folders are  not clear when I pass the mouse over it and the images too are not clear
  my graphic card is : Intel® G45/G43  and I didn't find the new updates of the driver in the Intel website
  I don't know if the problem is clear for you guys or not in the picture below

[IMG]http://i.stack.imgur.com/hbQN3.png[/IMG]

---

### Post by blm-ubunet on 2015-10-29
That intel graphics updating tool was really for users of the latest intel CPU/GPUs wanting the best (or any) performance.
The open source intel driver (i965) in 12.04 to 15.10 should be fine for G45.

AFAIU in rush to complete support for the important intel GPUs (HD) some of the bottom end devices got forgotten. I believe some the G45 features are now being implemented/completed.
What has possibly happened is that some obscure or new feature has been enabled in the driver & this has a bug for some h/w.
In the past, 2d acceleration corruption was normal for 945 chipset (i915) driver updates.

You could try disable SNA acceleration (all chipsets not just sandybridge) in favour of UXA..
I only know how to do this via /etc/X11/xorg.conf file.

There is a GUI program "driconf" that can assist with debug/disabling features.

---

### Post by mahdird5 on 2015-10-30
> **blm-ubunet said:**
> That intel graphics updating tool was really for users of the latest intel CPU/GPUs wanting the best (or any) performance.
The open source intel driver (i965) in 12.04 to 15.10 should be fine for G45.

AFAIU in rush to complete support for the important intel GPUs (HD) some of the bottom end devices got forgotten. I believe some the G45 features are now being implemented/completed.
What has possibly happened is that some obscure or new feature has been enabled in the driver & this has a bug for some h/w.
In the past, 2d acceleration corruption was normal for 945 chipset (i915) driver updates.

You could try disable SNA acceleration (all chipsets not just sandybridge) in favour of UXA..
I only know how to do this via /etc/X11/xorg.conf file.

There is a GUI program "driconf" that can assist with debug/disabling features.


Thank you, now everything is fine, and solved by disabling the SNA acceleration and I followed the temporary solution posted in the link below but the graphic quality is a little bit bad.

[http://ubuntuforums.org/showthread.php?t=2182033](http://ubuntuforums.org/showthread.php?t=2182033)

---

### Post by wightghost on 2015-10-30
Thank you. The link provided helped me to resolve the same issue in my newly installed 15.10.

---

### Post by blm-ubunet on 2015-11-07
I suggest that every couple of months re-enable SNA acceleration method to test if the problem has been fixed.

If you want to get closer to the fixes (& some other bugs!) you can use the "xorg-edgers" ppa, but you must be aware of the requirements & risks (stated in ppa webpage).

If you do use a custom (or any) "/etc/X11/xorg.conf" file than make a backup copy, system updates will trash or delete it at some point just after you forgot what it contained.

---

### Post by ywwg2 on 2015-12-25
I am also seeing new graphics problems with Intel and Ubuntu 15.10.  In the DJ software Mixxx, the audio waveform, which is drawn with OpenGL, fails to render for a couple seconds at a time occasionally.  Disabling SNA in favor of UXA also fixed the issue for me.  I tried installing the official Intel graphics drivers and it didn't fix the issue.  Hopefully this is a temporary regression.

---

