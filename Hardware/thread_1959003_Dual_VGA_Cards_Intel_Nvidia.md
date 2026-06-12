---
title: "Dual VGA Cards Intel/ Nvidia"
date: 2012-04-15
forum: Hardware
---

### Post by Reagentom on 2012-04-15
this is my first post in this forum.. I am new to Linux, just  installed Ubuntu 11.10 on my Sony Vaio VGN-Z12 with two graphic cards  Intel and NVidia Geforce 9300 GS. after the installation the lightdm works on Intel card but with very law  display quality. I installed Nvidia driver from the official website as  well as this PPA.
  **[B][SIZE=2]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/SIZE]**[/B]

  **[B][SIZE=2]sudo apt-get update[/SIZE]**[/B]

  **[B][SIZE=2]sudo apt-get install nvidia-current[/SIZE]**[/B]

  once I install the driver and run nvidia-xconfig which creates  xorg.conf file the xserver will not start with error "no screen" if I  delete the xorg.conf file then I am able to start the xserver normally  but with intel display (bad quality)
  Please Help

---

