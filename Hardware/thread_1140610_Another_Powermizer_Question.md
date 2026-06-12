---
title: "Another Powermizer Question"
date: 2009-04-27
forum: Hardware
---

### Post by john_gault on 2009-04-27
Hey. For the last 3 ubuntu releases I have been having trouble with Nvidia's powermizer feature. I is always stuck in the max performance mode and my gpu (8600gt) is running hot everyday. I want to lower it to mabye the desktop performance settings but I seem to be stuck. I searched around untill I found this:

Option  "RegistryDwords"    "PowerMizerLevel=0×3"

Which I am supposed to put in xorg.conf under device. When I do this I lose the graphics driver on reboot and it asks my to reconfigure graphics or restore xorg backup and I have to reinstall the driver. I tried to put it under the screen section in xorg.conf but this does not work either. What am I missing? Why does the powermizer feature not tune itself automatically?

---

