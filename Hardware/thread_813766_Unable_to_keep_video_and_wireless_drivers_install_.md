---
title: "Unable to keep video and wireless drivers install at once"
date: 2008-05-31
forum: Hardware
---

### Post by Blux08 on 2008-05-31
Hello. I am currently working on getting Ubuntu 8.04 installed and working on a HP dv6735nr laptop. I can get everything working, BUT....

I cannot have both the Atheros wireless and Nvidia drivers from the nvidia site installed at the same time. When i install either it disables the other.

Install Nvidia driver= After reboot Wireless is no longer installed.

Install Wireless driver again= after reboot nvidia drivers are uninstalled.

Anyways you get the picture. Is there a fix for this? Thanks

---

### Post by Blux08 on 2008-06-01
Bump

I've compared xorg.conf both before and after I installed the wireless drivers. It doesn't change. Still lost here.

---

### Post by prshah on 2008-06-03
> **Blux08 said:**
> 
I cannot have both the Atheros wireless and Nvidia drivers from the nvidia site installed at the same time. When i install either it disables the other.

Try this: After installing your nvidia drivers and enabling restricted drivers, open a terminal, and give the commands```

sudo modprobe ath_hal
sudo modprobe ath_pci
sudo /etc/init.d/networking restart
iwconfig
```

After the last command, your Atheros device should appear in iwconfig as "ath0", but may also be called wlan0, or something similar.

In case of any problems, post back here with the problem output as well as output of "iwconfig"

---

