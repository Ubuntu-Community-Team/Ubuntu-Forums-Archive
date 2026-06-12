---
title: "Curious nvidia driver issue"
date: 2013-08-26
forum: Hardware
---

### Post by mjh1275 on 2013-08-26
[COLOR=#333333][FONT=Lucida Grande]Hi guys I'm trying to install the nvidia-319 drivers with bumblebee on my laptop but I'm running into a curious issue. When I try to install the nvidia-319 drivers using sudo apt-get install it wants to pull the nvidia-325 drivers as well and ends up installing those instead. I'm wondering if there is a way to install 319 and not 325. I've already installed the bumblebee and xorg-edgers ppa's. My laptop is a Samsung NP700Z5C. Any help is appreciated. Thanks.

P.S. This seems to be the same no matter which derivative of ubuntu I try. I've also tried linux mint and elementary and get the same results. So this is not distro specific.[/FONT][/COLOR]

---

### Post by SweetAurora on 2013-08-26
Nvidia 325 has new optimus support, thats why it wants to install that over 319.

---

