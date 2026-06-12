---
title: "[SOLVED] nVidia driver installation"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by DeMus on 2008-12-30
This morning I tried to install the latest nVidia GeForce driver, "NVIDIA-Linux-x86_64-177.82-pkg2.run", but after doing so and after the re-boot the graphics driver does not show up as it should. Instead I get a standard VGA picture with an outlined cross as mouse cursor telling me to set things straight. I can choose the resolution I have (1280*1024) and I can select the nVidia card but I can not conform it so I leave the program with the cancel button. Then the GUI starts and I am left with a low resolution screen. 800*600 is the highest I can get.
When I use the nVidia settings program I get a message I don't have a compatible driver running, I should use nVidia-xconfig and after that restart X.
Whatever I do, it just won't work.
I did use the installation method for a new driver before but now it doesn't want to work. The method I use is:

Ctrl+Alt+F1 (to get Virtual Terminal)
username
password
sudo /etc/init.d/gdm stop (to stop the xserver)
password
sudo sh /path/to/driver/NVIDIA-Linux-xxxx.run
Accept the License
Let the driver compile the module into your kernel
(you need build-essential installed)
Let the driver reconfigure your xorg.conf file
Then: startx
Or:
sudo /etc/init.d/gdm start

As I said this is a way it has worked before. Is it possible that because of new updates of Ubuntu this does not work anymore?
What else could be a reason? I did install it on a freshly installed system without any strange things installed already.

DeMus

---

### Post by IQRules on 2008-12-30
I had used EnvyNG to fix similar issue. You might want to take a look.

---

### Post by DeMus on 2008-12-30
> **IQRules said:**
> I had used EnvyNG to fix similar issue. You might want to take a look.

What would I do without you? Still using the old driver, I guess.
Thank you so much, it works and it took me less than 10 seconds to install the driver. So fast, so easy, no problems at all.

Thank you and have a wonderful New Year.

---

