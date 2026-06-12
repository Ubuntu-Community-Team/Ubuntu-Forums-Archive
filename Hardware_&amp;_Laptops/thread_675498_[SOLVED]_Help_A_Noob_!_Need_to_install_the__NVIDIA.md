---
title: "[SOLVED] Help A Noob ! Need to install the  NVIDIA 169.09 ???"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by bigbrovar on 2008-01-22
I have been up all morning trying to install the latest Nvidia Graphic card  NVIDIA 169.09 
am trying to Use envy .. please can anybody assist me by giving me pointers on what steps i can take .. cus i dont want to mess up my xorg .. thanks

---

### Post by bigbrovar on 2008-01-22
Well i was able to get it installed painlessly by first installing evny from here [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) .. then i used it to install the Nvidia Driver ... it downloaded  and installed some needed dependencies then downloaded the older driver -Nvidia 169.07.. after which i allowed it to configure my Xorg Automatically.. then i rebooted. when i logged back in i downloaded the newest driver Nvidia 169.09 [http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run)
 saved it in my home directory. then i went into console ctrl + alt + 5, killed Xorg&gnome (sudo /etc/init.d/gdm stop) and then installed the latest drivers  (sudo sh NVIDIA-Linux-x86-169.09-pkg1.run). I told the nvidia installer to NOT to touch my xorg.conf file.. then i rebooted and enabled my restricted drivers .. .. all thanks to this  [http://www.nvnews.net/vbulletin/showthread.php?t=106637]("http://www.nvnews.net/vbulletin/showthread.php?t=106637") post by shoeunited in Nvidia forums

---

