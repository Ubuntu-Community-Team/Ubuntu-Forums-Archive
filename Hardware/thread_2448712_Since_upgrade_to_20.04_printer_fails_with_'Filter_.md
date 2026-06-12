---
title: "Since upgrade to 20.04 printer fails with 'Filter failed' message"
date: 2020-08-12
forum: Hardware
---

### Post by timgood on 2020-08-12
Hi guys - I have a Dell 1320c colour laser printer that I have been using happily for some years with the Fuji Xerox Docuprint C525 driver. Since I upgraded from 18.04 to 20.04 the printer fails with the message 'Filter failed' and I can print nothing. I have tried removing the printer, re-installing and finally removing the driver. 

When I tried to reinstall the .deb package for the c525 the package refused to install. I asked Mr Google and it seems that multiarch-support is no longer available in 20.04. I eventually managed to convert a .rpm package to a all.deb package which then installed and the driver became available in Cups and the printer configuration from system settings. I can set the printer up, the cartridge levels are detected, but attempting to print anything will result in 'Filter failed'. The help of your planet-sized brains would be of some great assistance if you could help me get the printer working again. Thanks.

---

### Post by jp734 on 2020-08-12
Can't help with your printer "filter" issue but I used to have a Dell Laser printer and I used lexmark driver. Apparently they were the same. Not sure if that is still the case but might be worth looking into.

---

### Post by timgood on 2020-08-13
After further research online, the filters are failing because they remain 32 bit and will not operate in a totally 64 bit environment. So I'm stuck unless there is some way of enabling multiarch-support on 20.04. Does anyone know if this is possible. Anyone want to buy a Dell 1320c?

---

### Post by slickymaster on 2020-08-13
*Thread moved to **Hardware**.*

---

### Post by timgood on 2020-08-13
Solved this by downloading and installing multiarch-support and libc6:i386 libncurses5:i386 libstdc++6:i386, removing driver and reinstalling i386 .deb and configuring printer in CUPS. Phew! But working now.

---

