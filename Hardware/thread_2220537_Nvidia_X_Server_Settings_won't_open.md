---
title: "Nvidia X Server Settings won't open"
date: 2014-04-28
forum: Hardware
---

### Post by patrick33 on 2014-04-28
Following a recent update to the nvidia-337 drivers on Xorg Edgers' PPA, I was able to install the proper drivers without losing access to my account afterwards. Now I've run into the problem my post title suggests. I was able to access the settings window immediately after the install, but once I switched the Prime profile to use the integrated Intel graphics it stopped displaying altogether.

Here's my specs
[COLOR=#000000][INDENT]Acer V3-772G-9460
[COLOR=#000000]Ubuntu 14.04x64[/COLOR]
[COLOR=#000000]Intel Haswell Core i7 4702MQ[/COLOR]
[COLOR=#000000]12GB DDR3[/COLOR]
[COLOR=#000000]Toshiba SSD primary[/COLOR]
[COLOR=#000000]Secondary HDD[/COLOR]
[COLOR=#000000]Nvidia Optimus GTX 760M w/ Prime
nvidia-337 Xorg Edgers[/COLOR][/INDENT]
[/COLOR]

---

### Post by patrick33 on 2014-04-30
.

---

### Post by steeldriver on 2014-04-30
Are there multiple versions of nvidia_settings_conf on the system? if so is the current one selected?

```

sudo update-alternatives --config nvidia_settings_conf

```

---

