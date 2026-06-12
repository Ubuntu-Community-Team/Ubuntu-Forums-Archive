---
title: "dell 266 latitude"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by Foodster on 2008-01-30
watchya folks.

wondering if anybody can help.i've just put alternate ubuntu on my old dell 266 so the girlfriend can use it as a word processor.i must say it worked like a dream,it even recognised the pcmia card.it would hardly run on win 98 so its been in a cupboard for two years.anyway i'm having problems with the resolution so was wondering if anyone has any xorg settings for the monitor.i've gone through the process through the terminal but i think its failing because i don't know what the monitor is.

thanks folks.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

---

### Post by overdrank on 2008-01-30
> **Foodster said:**
> watchya folks.

wondering if anybody can help.i've just put alternate ubuntu on my old dell 266 so the girlfriend can use it as a word processor.i must say it worked like a dream,it even recognised the pcmia card.it would hardly run on win 98 so its been in a cupboard for two years.anyway i'm having problems with the resolution so was wondering if anyone has any xorg settings for the monitor.i've gone through the process through the terminal but i think its failing because i don't know what the monitor is.

thanks folks.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:

HI and welcome, it appears that the memory for the graphics is only 2mb. Can you identify the graphics chipset with the lspci command in the terminal and look for VGA. Also I would check in the bios for the memory shared with the graphics and maybe it can be adjusted.

---

### Post by Foodster on 2008-02-01
cheers.i'll try that.

---

### Post by Foodster on 2008-02-01
can't alter the graphics  in the bios so i guess its more ram and a newer version of ubuntu.

---

