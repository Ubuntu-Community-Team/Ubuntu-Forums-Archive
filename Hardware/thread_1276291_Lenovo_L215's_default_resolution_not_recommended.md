---
title: "Lenovo L215's default resolution not recommended"
date: 2009-09-26
forum: Hardware
---

### Post by onlineapps on 2009-09-26
I just switched from a 20" Acer to a 21.5" Lenovo L215. The old Acer's default resolution was 1680x1050. The L215's is 1920x1080. However, whenever I turn on Ubuntu, it defaults to 1680x1050. (my graphics card is a Nvidia 9800GT with proprietary drivers) I even used Nvidia's setting tool; it would set it perfectly (even writing a xorg.conf file), but once I rebooted, back to 1680x1050.

Here's my xorg.conf: [http://pastebin.com/f74a3dd8a](http://pastebin.com/f74a3dd8a)

---

### Post by nixscripter on 2009-10-03
Try rebooting again, and when X starts before you fix the resolution manually, please post the contents of **/var/log/Xorg.0.log**

It is most likely X windows is ignoring the configuration file because of something the hardware is telling it (that the nVidia utility bypasses).

---

### Post by onlineapps on 2009-10-03
> **nixscripter said:**
> Try rebooting again, and when X starts before you fix the resolution manually, please post the contents of **/var/log/Xorg.0.log**

It is most likely X windows is ignoring the configuration file because of something the hardware is telling it (that the nVidia utility bypasses).

Yup. [http://pastebin.com/f67a2d483](http://pastebin.com/f67a2d483)

---

