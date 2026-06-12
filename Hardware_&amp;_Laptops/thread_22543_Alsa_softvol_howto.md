---
title: "Alsa softvol howto?"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by haaglin on 2005-03-28
I have a mainboard with onboard cmedia CMI9739 chipset. And i'm not able to control the volume. Can anybody please explain how i add the softvol pcm plugin provided from alsa? 

Code at the end of this page: 

[http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html)

---

### Post by Juergen on 2005-03-29
Create a ~/.asoundrc with the definition of a new device in it and then point your sound-apps to this device.
After you get it to work you can probably tweak something in /etc to make this system wide.

I haven't got it to work in Ubuntu, but here are some examples (in notes-section):
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=intel8x0)

---

