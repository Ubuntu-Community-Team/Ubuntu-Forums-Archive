---
title: "ATI radeon help!"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by Masterizaak on 2007-09-03
Ubuntu wont detect my graphic card, ati radeon 7000 card, I think I might need to install drivers, how do I do this?:confused:

---

### Post by w4ett on 2007-09-04
The ATI Radeon is only supported by the open source  xorg-driver-ati

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "ati" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This SHOULD get you to a GUI desktop.

---

