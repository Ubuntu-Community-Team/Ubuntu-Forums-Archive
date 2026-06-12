---
title: "Changing Video cards"
date: 2005-12-01
forum: General Help
---

### Post by andril on 2005-12-01
Am I gonna have any issues with booting into Ubuntu when I switch from my ATI Raedeon 9200SE to my new  GeForce FX 5200 256MB DDR AGP Video Card w/TV-Out? Please let me know what I need to do to prevent a reinstall. Thanks In Advance:)

---

### Post by invalid on 2005-12-01
All you will need to do, is switch over drivers to your new Nvidia card.
```
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable
```
and you should be good to go.

Cheers,
Cb

---

### Post by Bachstelze on 2005-12-01
Of course, you need to run those commands AFTER installing your nvidia card :)

---

### Post by invalid on 2005-12-01
Or right before you shutdown to install it, as the settings will not take effect until you restart X.

Cb

---

### Post by andril on 2005-12-07
New card installed and I am experiencing the same issues- take a look


Please help the edges are supposed to be rounded but that white tip persists.

---

