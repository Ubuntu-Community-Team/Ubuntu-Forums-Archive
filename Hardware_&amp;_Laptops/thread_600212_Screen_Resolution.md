---
title: "Screen Resolution"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by shoaibnawaz on 2007-11-02
I have Geforce Nvida 6600LE 256 MB RAM.
Desktop effects (including Beryl) is working very well. It means the updated drivers are installed. But my display settings are configured to 800x600 @ 50Hz. I want to increase the resolution to 1024x768 @ 70Hz and 1280x960 @ 70Hz.

How can I achieve it? In my last installation I achieved it 1280x960 @ 60Hz without any manual configuration. This time the scenario is same but GPU is not configured in the same manner for high resolution.

---

### Post by overdrank on 2007-11-03
> **shoaibnawaz said:**
> I have Geforce Nvida 6600LE 256 MB RAM.
Desktop effects (including Beryl) is working very well. It means the updated drivers are installed. But my display settings are configured to 800x600 @ 50Hz. I want to increase the resolution to 1024x768 @ 70Hz and 1280x960 @ 70Hz.

How can I achieve it? In my last installation I achieved it 1280x960 @ 60Hz without any manual configuration. This time the scenario is same but GPU is not configured in the same manner for high resolution.

Hi you can try ```
gksudo nvidia-settings
``` Then change your resolutions, but if you change your resolution just use the apply button. Because if you  use  " save to X configuration" this may change your xorg and disable the desktop effects. Good luck! :KS

---

