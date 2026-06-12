---
title: "no sound on thinkpad t60"
date: 2011-12-26
forum: Hardware
---

### Post by jmag21 on 2011-12-26
Hi,


After intalling ubuntu 11.10 on my Lenovo  Thinkpad T60 (1951), I have no sound. The sound card seems to be detected, I follow a french documentation that says to add the line options snd-hda-intel model = thinkpad at the end of the file  alsa-base.conf but nothing change. My sound card worked under windows and i'm a newby on Linux. If someone had got the problem and the problem is now solved, thanks to help me. Thank you.

---

### Post by jmag21 on 2011-12-27
I found the solution.
**We have to enable the volume control buttons:**

sudo gedit /etc/rc.local
 and add the line:

cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask  /sys/devices/platform/thinkpad_acpi/hotkey_mask 

thanks

---

