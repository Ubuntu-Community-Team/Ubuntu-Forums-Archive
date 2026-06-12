---
title: "Acer Aspire 5000 from-scratch setup - Ubuntu 9.10"
date: 2009-12-27
forum: Hardware
---

### Post by brianmc on 2009-12-27
I just finished getting an Acer Aspire 5000 set up with the current Ubuntu 9.10.

There were several problems, and as-of-now, installing from a live CD, connecting to the Internet, and applying all updates will leave the system with X failing to start.

As I eventually found, the machine I have here has SiS hardware for graphics. This is not correctly supported on the -14 kernel installed from a live CD - a limited palette is available and the display of any image is incorrect. Upgrade to the now-current -16 kernel breaks this completely.

The required fix is to edit /etc/modules and, on a line on its own, add "sisfb".

Once this is in place, and the hardware driver for WiFi added (Which a 9.10 live CD recognises but does not contain), then the machine will happily upgrade to a fully current 9.10 install.

---

