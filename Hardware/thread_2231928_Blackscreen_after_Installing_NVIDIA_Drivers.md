---
title: "Blackscreen after Installing NVIDIA Drivers"
date: 2014-06-28
forum: Hardware
---

### Post by TJSL on 2014-06-28
System: Lenovo y510p (single GPU, no SLI), clean install on 14.04
lspci | grep VGA shows GeForce GT 755M

Command line:
```
sudo apt-get purge nvidia* -y
echo -ne '\n'| sudo add-apt-repository ppa:org-edgers/ppa #automate "enter"
sudo apt-get update
sudo apt-get install nvidia-current -y
```

---

### Post by TJSL on 2014-06-28
UPDATE: Black screen was traced to issues with numlockx; and missing menus after login to NVIDIA driver 

Numlockx:
The location of the configuration file for numlockx changed in Ubuntu 14.04. My black screen was caused by a configuration script written for 13.10. Running the commands below fixed the black screen.

```

sudo apt-get install numlockx
sudo sh -c "echo 'greeter-setup-script=/usr/bin/numlockx on' >> /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf"
```

NVIDIA Driver:

Changing nvidia-current to nvidia-331 replaced the missing menus.


```
sudo apt-get purge nvidia* -y
echo -ne '\n'| sudo add-apt-repository ppa:xorg-edgers/ppa #automate "enter"
sudo apt-get update
sudo apt-get install nvidia-331 -y
```

---

