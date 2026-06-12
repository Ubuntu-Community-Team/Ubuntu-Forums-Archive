---
title: "Problem with NVIDIA 310 driver"
date: 2013-01-22
forum: Hardware
---

### Post by Piccy on 2013-01-22
I installed the Nvidia 310 experimental driver from Additional Drivers. Reason was because I installed Steam and Serious Sam 3 was running at a low frame rate. Anyway, after installing the driver and reboot, I get no GUI. Just a CLI. Is there anyway to revert back to a more stable driver version.

Running 12.04LTS
Nvidia GTX 285

---

### Post by Lightning Dragon on 2013-01-22
Hello,

You aren't the only one. You will have to use CLI to uninstall the driver you installed.

---

### Post by papibe on 2013-01-22
Hi Piccy.

> **Piccy said:**
>  Is there anyway to revert back to a more stable driver version.

Sure there is.

Uninstall all Nvidia packages:
```
sudo apt-get purge nvidia-*
```
Then remove the Xorg config file:
```
sudo rm -rf /etc/X11/xorg.conf
```
Then restart.

You should boot into the GUI using the Nvidia open source driver (nouveau). Once on the desktop, install the recommended Nvidia driver, usually named nvidia-current (recommended).

Before you reboot to take effect. Create a custom Xorg config file:
```
sudo nvidia-xconfig
```

Another reboot, will get you using the stable Nvidia proprietary driver.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Piccy on 2013-01-23
Thanks papibe

That worked!!!!!

BTW the additional drivers window tells me that the nvidia-current driver is activated but its not in use

Whats up with that?

Any way of telling what driver is in use?

---

### Post by papibe on 2013-01-23
Sure there is.

Could you post the result of these 2 commands?
```
lsmod | grep -i nvidia

lspci -nnk | grep -iA2 vga
```
Regards.

---

