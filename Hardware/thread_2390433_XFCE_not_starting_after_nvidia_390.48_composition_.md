---
title: "XFCE not starting after nvidia 390.48 composition pipeline activation"
date: 2018-04-28
forum: Hardware
---

### Post by una.trindade on 2018-04-28
Hello Folks,

After I changed the Nvidia Driver settings, checking the "Force Composition Pipeling" feature, I can even enter the GDM but after setting the password I only see the wallpaper and XFCE does not load. I am using the NVIDIA Proprietary Driver 390.48

specs:

Using Xubuntu 18.04
XFCE 4.12

NVIDIA GTX1060
RYZEN 1700
ASUS B350F GAMING

---

### Post by Yellow Pasque on 2018-04-30
Maybe take a look at this thread: [https://devtalk.nvidia.com/default/topic/1029381/linux/black-screen-at-desktop-login-gtx-750-ti-390-25-/1](https://devtalk.nvidia.com/default/topic/1029381/linux/black-screen-at-desktop-login-gtx-750-ti-390-25-/1)

---

### Post by una.trindade on 2018-04-30
> **Temüjin said:**
> Maybe take a look at this thread: [https://devtalk.nvidia.com/default/topic/1029381/linux/black-screen-at-desktop-login-gtx-750-ti-390-25-/1](https://devtalk.nvidia.com/default/topic/1029381/linux/black-screen-at-desktop-login-gtx-750-ti-390-25-/1)
[COLOR=#000000]Thanks! I'll check later if there's a solution for this problem and If so I'll post here as solved.[/COLOR]
:wink:

---

### Post by una.trindade on 2018-04-30
Solved:

```
I did manage to get things sorted out regarding xorg with  CompositionPipeline enabled on boot by deleting the secondary display  position values in the displays.xml file for xfce in  /home/XXXXX/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml  (deleting that file also works).  

```

It works! Thank you!

---

### Post by Yellow Pasque on 2018-04-30
You're welcome

---

