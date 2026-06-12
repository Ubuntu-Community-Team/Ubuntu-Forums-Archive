---
title: "touchpad completely doesnt work"
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by sublime on 2006-01-25
i've been reading through a lot of the threads about touchpad problems and it seems its fairly common for the alps touchpads to not have vertical scrolling.  however my touchpad completely doesnt work.  i installed and ran tpconfig and it detects it.  heres the message it gives me:

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

anyone have any ideas?

---

### Post by stangbang on 2006-01-25
You might want to make sure that the touchpad is not disabled in the bios. Also most notebooks have a switch to turn the touchpad on or off. such as on mine Fn+F4. You might want to double check this. Also did the touchpad ever work in ubuntu, or any other OS? Also what model of laptop are you using, and what is the your output when you enter cat /proc/bus/input/devices

---

### Post by sublime on 2006-01-25
omg im retarded.  yeah i switched must have switched it off.  however in my retardedness i used the configuration guide in a stickie in the hardware forum and edited my xorg.conf file and now my graphical interface doesnt work.  i can tell this is gonna be a fun day.

---

### Post by 1nf3rn0 on 2006-01-25
im having same prob on ma fuji siemens amilo pro v7010 but fn and f4 aint workin away to try the bios now but if not any ideas peeps?

---

### Post by sublime on 2006-01-25
for me it wasnt fn + f4 it was fn + f9.  look at the keys for a little picture that looks like a touchpad

---

