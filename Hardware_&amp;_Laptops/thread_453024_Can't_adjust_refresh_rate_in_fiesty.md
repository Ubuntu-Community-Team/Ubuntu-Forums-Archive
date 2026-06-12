---
title: "Can't adjust refresh rate in fiesty"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by pablo66 on 2007-05-23
I have a Dell D620 with a nVidia quatro NVS110, and the native refresh rate is 60hz at 1440x900 resolution and it's only running at 50hz.
i ran sudo gedit /etc/x11/xorg.conf and it opened a blank document, there is nothing there.  Any other ideas?

---

### Post by joriad on 2007-05-23
sudo gedit /etc/x11/xorg.conf should read sudo gedit /etc/X11/xorg.conf.
As you may notice the X in X11 is capitalized.

---

### Post by WiFi Ed on 2007-05-24
There's a bug related to refresh rate reporting and nvidia cards. If Ubuntu is reporting 50Hz, it's more likely you're running at 75Hz. See what xvidtune reports, or if your monitor has an "Information" screen, see what it says.

---

