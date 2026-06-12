---
title: "Nvidia Drivers fail to recognize my Geforce Go 7700"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by AltF4 on 2007-10-22
I have an ASUS A8js, Nvidia Geforce go 7700, and have just finished installing the recently released Ubuntu 7.10. 

My issue is that after successfully installing the Nvidia drivers for my card (1.0-9755) and restarting my computer, i am greeted with a window telling me that my monitor and or card have not been recognized properly and that i should run in low graphics mode.

I know for sure this isn't my bios because the card works in XP, and i've tried using Envy to do a re-installation of the driver and configuration of the Xorg.conf file and came to the same problem. I have also tried using an older version of the driver (1.0-9746), with the exact same result.

I'm a linux noob so i may be missing something blatantly obvious so feel free to suggest anything you can think of. Thanks in advance for any help.

---

### Post by mrfuzzemz on 2007-10-24
> **AltF4 said:**
> I have an ASUS A8js, Nvidia Geforce go 7700, and have just finished installing the recently released Ubuntu 7.10. 

My issue is that after successfully installing the Nvidia drivers for my card (1.0-9755) and restarting my computer, i am greeted with a window telling me that my monitor and or card have not been recognized properly and that i should run in low graphics mode.

I know for sure this isn't my bios because the card works in XP, and i've tried using Envy to do a re-installation of the driver and configuration of the Xorg.conf file and came to the same problem. I have also tried using an older version of the driver (1.0-9746), with the exact same result.

I'm a linux noob so i may be missing something blatantly obvious so feel free to suggest anything you can think of. Thanks in advance for any help.

I've got the same notebook and card.  Try installing the latest NVidia driver with Envy (100.14.19 or 100.14.23).  I gave the author of Envy the device and hardware ID for our cad so there should be no trouble with detection.

---

### Post by Cyber-J on 2007-10-24
Sadly nothing seems to work for me. Tried all of that above and I still cannot get the proper resolution of 1400x900 on  my Samsung 940mw LCD. =( I've always had this problem with prior Ubuntu releases but had it resolved once I installed the proprietary driver. Not so with Gutsy. Something in this release of Ubuntu has completely broken the dual display/external display detection. :confused: So for now, I just use the "Vesa" driver and I can at least get 1024x768 on the Samsung LCD which is better than nothing. Hopefully this will be fixed soon or I'll be departing Ubuntu for another distro.

---

### Post by mrfuzzemz on 2007-10-24
> **Cyber-J said:**
> Sadly nothing seems to work for me. Tried all of that above and I still cannot get the proper resolution of 1400x900 on  my Samsung 940mw LCD. =( I've always had this problem with prior Ubuntu releases but had it resolved once I installed the proprietary driver. Not so with Gutsy. Something in this release of Ubuntu has completely broken the dual display/external display detection. :confused: So for now, I just use the "Vesa" driver and I can at least get 1024x768 on the Samsung LCD which is better than nothing. Hopefully this will be fixed soon or I'll be departing Ubuntu for another distro.

How and what have you attempted to install and what error messages are you getting?

---

