---
title: "multi video card, no additional outputs"
date: 2011-12-25
forum: Hardware
---

### Post by lookitscook on 2011-12-25
I'm running Xubuntu 11.10 on a G5 (PPC) with stock Radeon 9600 and an additional Radeon 7000 PCI, default open-source drivers. When I added the 7000 it is recognized, but no additional outputs are detected by randr when a monitor is connected. Any suggestions? 

"lspci | grep VGA" returns the following:

```

0000:f0:10.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0001:06:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

```

---

