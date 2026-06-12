---
title: "latest nvidia graphics driver"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by ZeldaFan on 2007-06-04
Going to the the nvidia website I found that the latest available graphics driver for my Geforce go 7600 graphics card is 1.0-9755. Looking at what graphics card I have, I have 1.0-9631, which was installed when I enabled the nvidia drivers after installing Feisty. I want to update my drivers to latest version, but I dont want to mess with anything unless I am sure that I am not going to mess up my computer. If I just follow the instruction on the web site I should be fine right? Do I have to update anything else or change anything else, like my kernel? I run Ubuntu Studio, so I have the generic and low latency kernel. By the way, I am a relatively new Ubuntu user.

---

### Post by mikewhatever on 2007-06-04
I think your best shot is to use [envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Disable the current driver or even uninstall it first.
By the way, I've done just that for geforce 7400 go and see no difference in performance.

---

### Post by steveneddy on 2007-06-04
I posted the same question [here]("http://ubuntuforums.org/showthread.php?t=464540").

---

### Post by mikewhatever on 2007-06-04
> **steveneddy said:**
> I posted the same question [here]("http://ubuntuforums.org/showthread.php?t=464540").

The new envy version does not remove the restricted modules. In my case, the new ones were pulled in along with the kernel update, and the driver worked as it did before.
Do not forget to:
1)Disable desktop effects if any.
2)Disable the current 9631 driver.
3)Backup xorg because envy will ask to reconfigure it. (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup)
4)Uninstall 9631driver prior to installing the newer one. Envy can do both.

---

