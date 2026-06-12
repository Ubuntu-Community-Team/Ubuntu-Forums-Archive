---
title: "Triple monitor laggy with gnome"
date: 2023-06-01
forum: Hardware
---

### Post by lobopodia on 2023-06-01
Triple monitor works smoothly with HP dc7900 Win10, but stutters when moving windows in ubuntu 22.04.2 LTS gnome 42.5

I did some tests:

Onboard VGA Intel Q45/Q43 GPU works smoothly with one screen when Nvidia NVS300 PCI card is removed.

NVS300 dual display works smoothly with only two screens when selected as  primary display device in BIOS and the onboard VGA is disconnected.

It appears gnome can't handle both at the same time.

Any advice please

---

### Post by lobopodia on 2023-06-01
It appears gnome uses the Wayland display driver, which cannot run a dual GPU system properly.

Can anybody help with a work around?


[https://gitlab.gnome.org/GNOME/mutter/-/issues/2303](https://gitlab.gnome.org/GNOME/mutter/-/issues/2303)
[https://gitlab.gnome.org/GNOME/mutter/-/issues/2295](https://gitlab.gnome.org/GNOME/mutter/-/issues/2295)
[https://gitlab.gnome.org/GNOME/mutter/-/issues/2166](https://gitlab.gnome.org/GNOME/mutter/-/issues/2166)

---

