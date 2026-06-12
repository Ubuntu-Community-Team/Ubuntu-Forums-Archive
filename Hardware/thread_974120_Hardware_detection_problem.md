---
title: "Hardware detection problem"
date: 2008-11-07
forum: Hardware
---

### Post by xeperis on 2008-11-07
Hi, I have ubuntu 8.10 on DELL XPS 1530, when i installed it the hardware manager even managed to configure my wireless and video drivers but after fidelling with beryl i've crashed my X server, which i fixed by wiping out and reinstalling the xorg core and nvidia drivers. After that the hardware manager does not detect my wifi card, whenever i turn it on/off. How can i force detection on this thing?

---

### Post by phidia on 2008-11-07
What wireless card do you have?

> lshw -C network & > iwconfig

---

### Post by xeperis on 2008-11-07
It's 1390 802.11 b/g Mini-card, it's says unclaimed in hardware list

Oh, and i tried the ndiswrapper, to install the drivers i used for winxp, but it didn't work

---

