---
title: "Additional monitor not working properly with laptop"
date: 2011-07-23
forum: Hardware
---

### Post by MrSlaggers on 2011-07-23
I have an HP Pavilion dv6 laptop, and and a 23 inch Dell monitor that I would like to use as a second monitor for my setup. The resolution on the laptop is 1366 x 768 (16:9) and the resolution on the Dell monitor is 1920 x 1080 (16:9).

When I attempt to add the second monitor to the left side of the laptop monitor in Monitor Preferences, I get this error: "**The selected configuration for displays could not be applied** requested position/size for CRTC 147 is outside the allowed limit: position=(1920,312), size=(1366, 768 ), maximum=(1920, 1920)"

I noticed in this thread [http://ubuntuforums.org/showthread.php?t=1771718](http://ubuntuforums.org/showthread.php?t=1771718) that moving the second monitor on top or below the laptop monitor works, and this is true for me as well, however this is not the behavior I am looking for. I would like to make it so each monitor acts as one of my virtual desktops.

---

### Post by MrSlaggers on 2011-07-24
bump

---

### Post by MrSlaggers on 2011-07-25
bump

---

### Post by MrSlaggers on 2011-07-26
bump

---

### Post by MrSlaggers on 2011-07-27
bump

---

### Post by MrSlaggers on 2011-07-29
Okay I was able to fix this issue. I first added the monitor in ATI Catalyst Control Center which is under System -> Preferences if you have the driver installed. Once you have done that and restarted the computer, you can add the monitor under the normal System -> Preferences -> Monitors setting.

---

### Post by vvasuki on 2012-05-06
This helped me very much. Thanks!

---

