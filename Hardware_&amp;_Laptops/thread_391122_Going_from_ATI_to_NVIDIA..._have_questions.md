---
title: "Going from ATI to NVIDIA... have questions"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by benton on 2007-03-22
Hi there! I have a PC running Edgy with an ATI Radeon 9000 AGP card. I have not downloaded any closed-source drivers from ATI, the card is using the open source drivers installed by default.

Now a new NVIDIA GeForce 6200 is in the mail. I'm new to Linux so I have some questions about the upgrade. In Windows I'd uninstall the ATI drivers, replace the card, and boot Windows to let it install it's default drivers. Then I'd install the latest from the NVIDIA site.

Should I follow the same procedure in Ubuntu Edgy? If so, how can I uninstall the ATI drivers prior to replacing the card? When booting up with the new card... am I going to face some problems because my xorg.conf file is configured for the ATI drivers?

I appreciate any guidance you can provide me about this upgrade.

Thanks in advance,

-Benton

---

### Post by mikewhatever on 2007-03-22
envy is by far the best way of installing the latest nvidia/ati driver

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by benton on 2007-03-22
Thanks, I knew about Envy but... should I uninstall the ATI drivers first... or just boot with the new card and Envy will take care of this?

Thanks!

---

### Post by mikewhatever on 2007-03-22
Try the second, don't think ati drivers will work for nvidia.

---

