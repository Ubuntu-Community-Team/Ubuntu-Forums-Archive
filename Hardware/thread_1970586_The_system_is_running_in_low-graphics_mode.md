---
title: "The system is running in low-graphics mode"
date: 2012-05-01
forum: Hardware
---

### Post by Kristapszs on 2012-05-01
Hi!
I have laptop HP probook 5320m with intel graphics and ubuntu 12.04 lts. After update i restarted my computer and get this message : The system is running in low-graphics mode . I searched this problem , but nothing helped me. 

I tried comandlines: 

sudo apt-get update
sudo apt-get -d install --reinstall gdm
sudo apt-get remove --purge gdm
sudo apt-get install gdm
sudo apt-get remove --purge xserver-xgl compiz compiz-plugins compiz-core compiz-manager csm cgwd cgwd-themes
sudo apt-get install --reinstall compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins libcompizconfig0
sudo dpkg-reconfigure -phigh xserver-xorg

and it was succesfull , i booted ubuntu, but after i restarted it , i get the same error. And comandlines did not work second time.
I decided to reinstall ubuntu, but also my usb stick did not booted.

IMPORTANT UPDATE!!! i choosed GDM not lightgdm and everything works. Any ideas?

---

