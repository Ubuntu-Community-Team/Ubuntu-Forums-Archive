---
title: "Monitor Samsung / xorg.conf"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by bach on 2005-06-10
I have recently installed Ubuntu 5.04 on my desktop. My monitor is Samsung SyncMaster 955DF. Here is what I have in /etc/X11/xorg.cong

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

What should I add (refresh rates and, especially, modelines) in order to optimize it for my monitor? (I note the image "trembles" a little...) 

Thanks in advance.

---

### Post by giageo on 2005-06-10
You should add "HorizSync xx-xx" and "VertRefresh xx-xx" where xx are the horizontal and vertical frequency values that correspond to your monitor. You should also add (if it doesn't already exist) the native resolution of your monitor at the Screen section.

---

