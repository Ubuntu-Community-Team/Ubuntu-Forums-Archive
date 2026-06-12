---
title: "Possible Source of Sound Conflict with Intel Sound?"
date: 2009-01-15
forum: Hardware
---

### Post by dmorg78 on 2009-01-15
I'm running an Asus P5QL-EM motherboard with an Intel G43 chipset on 8.10. The board has integrated sound and graphics. I have a PCI-E Nvidia graphics card which I use as my primary display adapter. Integrated Intel graphics is disabled.

I get NO sound with Ubuntu 8.10. I have tried every fix possible and am still yet to get it working, but I believe I know why.

When I remove my Nvidia graphics card, sound comes back straight away. I use the integrated Intel graphics and have no sound problems.

Problem is I dual boot and cant play games on the nvidia. Not quite sure what to do from here.

Does anyone else with the sound problems also have a pci-e graphics card installed? Does anyone have any idea how to resolve this? In the BIOS i have tried PNP OS set to both YES and NO but still no luck. Not sure what else to try. 

Any help would be hugely appreciated

Cheers
Dave

---

### Post by Cyriis on 2009-01-15
I too have no sound with my Intel integrated sound card on my Gateway laptop. I still have it when I boot from Windows XP home, but Ubuntu can't do sound.

---

### Post by Jim di Griz on 2009-01-22
Exactly the same problem!

I did find this:
[http://www.phoronix.com/scan.php?page=news_item&px=NjgzNg](http://www.phoronix.com/scan.php?page=news_item&px=NjgzNg)

Which seems to suggest a solution, but to be honest I havn't the faintest idea how to insatll any of the linked patches!

:(

---

### Post by markbuntu on 2009-01-22
The problem is that the Nvidia card has its own hdmi sound device and that is being found and listed first and so becomes the default sound hardware. There are a number of ways to deal with this issue but first you need some tools and an idea about how to use them. You can find help for that here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

