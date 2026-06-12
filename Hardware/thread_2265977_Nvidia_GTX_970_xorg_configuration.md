---
title: "Nvidia GTX 970 xorg configuration"
date: 2015-02-19
forum: Hardware
---

### Post by courtney2 on 2015-02-19
So I just purchased the Asus VG248 monitor that supports 144Hz refresh rate, and I figured out how to enable the 144Hz refresh rate in the Nvidia X Server Settings application, however, I can't figure out how to get it to save and reload on startup, as it will default back to 60Hz each time. There is no xorg.conf file, as I believe it is being replaced by the nvidia-xorg.conf file. What's the best way to save this? So far I've tried opening up the nvidia-settings as root and saved it to nvidia-xorg.conf with the "Save to X Configuration File", but that didn't work..I'm wondering if that only takes effect if I log in as root? End goal is to have it always start up at 144Hz.

Hardware:
MSI GTX 970
Asus VG248 with DisplayPort connection to GPU
Ubuntu GNOME 14.10

---

### Post by courtney2 on 2015-02-23
bump

---

