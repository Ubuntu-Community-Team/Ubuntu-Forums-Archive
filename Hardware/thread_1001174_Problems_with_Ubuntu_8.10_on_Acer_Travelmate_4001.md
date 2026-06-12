---
title: "Problems with Ubuntu 8.10 on Acer Travelmate 4001"
date: 2008-12-03
forum: Hardware
---

### Post by teranex on 2008-12-03
Hi,

Yesterday I installed Ubuntu 8.10 on an Acer Travelmate 4001WLMi, but i have some problems:

* Whenever i shutdown the laptop, i see a black screen with "acpid exiting..." (and a blinking cursor), and the laptop is not turned of (i can turn it of by pressing and holding the power button for a few seconds. I guess this has something to do with ACPI, but i have no idea how to fix this

* Just after the clean install my x-server would freeze: i could move the mousepointer, but it didn't move smoothly, i could not type and i could click (although somethimes i could manage to login). After googling and browsing this forum, i modified my xorg.conf file to use the VESA driver, and now i can login and use my laptop, but the screenresolution is completely wrong (it is 1024x768, while it should be 1200x800) and i can't change it, and i'm also not able to enable Compiz. I already tried to install the ATI drivers for the graphics card of the laptop and modify the xorg.conf file, when whenever i choose another driver in the config-file the x-server wont start anymore...

A friend of mine has the exact same laptop as i do which he also reinstalled with Ubuntu 8.10 just a week ago. He had problems with ACPI, which he had to disable using a kernel param before he could install (with ACPI enabled his laptop would crash). But his graphics card works without any problems and his xorg.conf-file is allmost empty.

any help is very much appreciated as i have no idea how to fix these issues....

---

