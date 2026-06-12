---
title: "NO GUI -HP nx6125"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by jitesh on 2006-06-05
After installation of Ubuntu Linux on an HP nx6125, the system does not load the GUI, what do I do?

---

### Post by Davor281 on 2006-06-05
Try loading in failsafe mode, then edit the xorg.conf file in /etc/X11/, and disable video acceleration in the video device asection

 > Option "NoAccel" "True"

After that you should be able to boot into GUI.

For more info about Ubuntu on NX6125 check here - [http://kastorhq.info/hpnx6125/](http://kastorhq.info/hpnx6125/)

---

### Post by jitesh on 2006-06-06
Edited the file, but still no luck. I then also edited, the resolution from 1024x768 to 640x480, and still no luck. Any further ideas.

---

### Post by jitesh on 2006-06-06
It worked, edited the file wrongly. Thanks

---

