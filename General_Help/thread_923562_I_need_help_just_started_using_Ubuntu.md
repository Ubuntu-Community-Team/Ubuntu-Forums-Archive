---
title: "I need help just started using Ubuntu"
date: 2008-09-18
forum: General Help
---

### Post by MADMAG7_62 on 2008-09-18
I dont know if this has been asked before and answered. But i am new to ubuntu or any form of linux. I am try to install gnome gui on ubuntu linux and not sure how this is done. I am currently running Ubuntu on vmware workstation and as soon as i go on to the OS i lose my internet connection on usb. So when i type in sudo apt-get install xserver-xorg xfonts* gnome. it tell me it cant find said file. What must i do.

Thanks
Brian

---

### Post by Tom--d on 2008-09-18
Gnome is installed on Ubuntu. Its the GUI.

Kubuntu has KDE on it (another Desktop environment, gnome is an DE)
Xubuntu has Xfce on it.
Ubuntu has Gnome on it.

---

### Post by prshah on 2008-09-18
> **MADMAG7_62 said:**
> 
as soon as i go on to the OS i lose my internet connection on usb. So when i type in sudo apt-get install xserver-xorg xfonts* gnome. it tell me it cant find said file.

You must give more information. Have you used an ubuntu-server CD by any chance? If you use a "desktop" CD, the GUI environment (gnome) and X server (xserver-xorg) will be installed by default.

If you're trying to put a GUI on a server CD installed edition, you can try the command ```
sudo apt-get install ubuntu-desktop
```. This requires either an Internet connection or the "alternate" Ubuntu desktop CD.

Coming to the Internet connection issue: If you cannot use your USB modem in (virtual) ubuntu, setup a NAT on the host machine with vmware, and in Ubuntu, it should then "just connect".

---

