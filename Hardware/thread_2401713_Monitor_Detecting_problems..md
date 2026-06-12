---
title: "Monitor Detecting problems."
date: 2018-09-21
forum: Hardware
---

### Post by loknath-dhar on 2018-09-21
Ubuntu 18.04 Detects 2 monitors when I only have** _one_.** My monitor model is LG *LG22MP68VQ-P*. HDMI supported. I have to rearrange the settings to get the screen. Can anyone help me out?

---

### Post by loknath-dhar on 2018-09-21
Run ```
xrandr -q
``` and find the false display.
Then get the full name from
[PHP]ls /sys/class/drm[/PHP]
It will look something like "card0-DSI-1".
Edit [HTML]/etc/default/grub[/HTML]
and change
GRUB_CMDLINE_LINUX= 
to include
"video=DSI-1:d" 
or the equivalent of the card name you got from the ls command above and then finally run
sudo update-grub 
and reboot.
     




this solved my problem. Thank you guys.

---

