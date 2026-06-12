---
title: "Acer TravelMate: Enable touchpad every time I boot."
date: 2013-12-18
forum: Hardware
---

### Post by logan-baron on 2013-12-18
Good morning. I have an Acer TravelMate (specific model escapes me right now, if requested I can check after work), and I'm having an issue where I need to press a key combination (Fn + F7) to enable the touchpad every time I start Ubuntu. I'm not sure what's causing it, but if anyone else has had this issue, or if anyone would know how to fix it (Drivers? A script to send a key combination on boot?), please let me know. Normally I wouldn't worry and just press the key combination, but this notebook is a gift to someone who would very quickly grow tired of doing this, or possible even forget that it needs to be done leading her to believe that the notebook is broken.

---

### Post by logan-baron on 2013-12-19
Okay, I managed to find a fix. In my /etc/modprobe.d directory I had edited a file (I forget which it was now) and added the line:

blacklist acer-wmi
After that, everything worked between reboots.

---

