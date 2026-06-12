---
title: "AGP 7699GS issue"
date: 2007-12-02
forum: Hardware &amp; Laptops
---

### Post by nimeshchandran on 2007-12-02
hello guys i installed ubuntu 7.04. i got a 7600 gs AGP card... so i installed nvidia-glx-new.. after that as instructed i ran the command "nvidia-glx-config enable"... after that i restarted the computer... but from then on the graphics system won't start... i mean it crashes whenever i give the command startx... going through the xorg.conf file i saw that its given pci for the nvidia card.. is it because the card is agp that the driver is not working?? what should i do????

---

### Post by Peturrr on 2007-12-13
Having the same problem. Looks like Ubuntu can't handle the card. Very strange.

---

### Post by Peturrr on 2007-12-13
Have found the solution for my problem, hopefully it works for you too.

My problem was that the card doesn't has a fan but a heatsink. Somehow the linux drivers check if the powercable to the fan is attached/working. Because there is no fan, the cable isn't there and X won't start.
Putting the following in /usr/X11/Xorg.conf under the section "Device", made X start up in my case.
```
Option "NoPowerConnectorCheck" "true"
```Please let me hear if it still doesn't work, I will try to help you figuring out what is wrong. Please attach your /var/log/Xorg.0.log file.

---

