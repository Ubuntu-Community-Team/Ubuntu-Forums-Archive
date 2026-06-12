---
title: "MSI M635 Laptop Suspend Mode &amp; Graphic Card Problems"
date: 2011-04-28
forum: Hardware
---

### Post by kevinhth on 2011-04-28
I have a MSI M635 Notebook Computer with AMD Turion 64 MT-32 CPU and ATI Mobility Radeon X700 Graphic Card. Both Ubuntu Desktop 10.10 & 11.04 32-bit have same issues.

1. It goes into Suspend Mode without problem. But, after pressing power button, power indicator stops flashing but no screen shown up. No response on any key. I can only turn off the power then restart the laptop.

2. Low graphic performance. It appears graphic driver has not been properly installed. I’ve entered following commands on Terminal:

$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X700 (PCIE) [1002:5653]
$ glxinfo | grep vendor
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils

I’ve checked AMD/ATI website. It did not provide Mobility Radeon Drivers for laptop computers. Then, I checked MSI website, it did not have any Ubuntu/Linux drivers for this model.

Please help. Thanks so much.

---

