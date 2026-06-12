---
title: "How to install drivers for Nvidia GeForce GTX 950M on Ubuntu 14.04 LTS?"
date: 2016-05-20
forum: Hardware
---

### Post by ariel16 on 2016-05-20
How to install drivers for Nvidia GeForce GTX 950M on Ubuntu 14.04 LTS?

---

### Post by Bashing-om on 2016-05-20
ariel16; Hello;

Nvidia recommends the 361 version driver. in 14.04 we get that driver from our trusted PPA .
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)

procedure:
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt full-upgrade
sudo apt-get install nvidia-361
sudo reboot

```

The gamers indicate they get better performance with the 364 version driver.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

