---
title: "Nvidia X Server Settings Issue in 8.10"
date: 2008-11-01
forum: Hardware
---

### Post by EmyrB on 2008-11-01
Hi All

Just upgraded my 8.04.1 install to 8.10. So far so good except that I have an issue with my graphics card. I have a GeForce 8400GS and I have installed the restricted Nvidia driver 177.80. My monitor is a Hanns.G HN198D which has a maximum res of 1280 x 1024. I can set the resolution amnually in the app but how do I get the X Server Settings app to actually use the maximum res all the time? I have set my xorg.conf file up but it still won't take the settings it always sets itself to 1024 x 768 even though the screen resolution app is set to 1280 x 1024.

If it cannot be done, can I uninstall the app and use the xorg.conf instead?

Cheers

EmyrB

---

### Post by EmyrB on 2008-11-03
Never mind, I used the 173 driver and was able to use the monitor's highest resolution.

---

### Post by tuxxy on 2008-11-03
You could try setting the resolution in **nvidia-settings > xserver display configuration > resolution**

---

