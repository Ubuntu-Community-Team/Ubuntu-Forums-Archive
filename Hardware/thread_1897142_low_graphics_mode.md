---
title: "low graphics mode"
date: 2011-12-18
forum: Hardware
---

### Post by pko76 on 2011-12-18
my graphic card is nvidia 6600gt and the os is ubuntu 10.04.the problem is that the proprietary drivers don't work.i get an error message after grub and i must select low graphics mode from the menu in order to load ubuntu.

---

### Post by BC59 on 2011-12-18
Did you try install them through Synaptic? Install Synaptic through Ubuntu Software center and search "nvidia". Then install the proposed drivers.

---

### Post by pko76 on 2011-12-18
> **BC59 said:**
> Did you try install them through Synaptic? Install Synaptic through Ubuntu Software center and search "nvidia". Then install the proposed drivers.
i follow your advice but the problem continues.to be more specific the error message says that nvidia kernel module failed to load

---

### Post by BC59 on 2011-12-18
In that case you have to uninstall the old driver and install the new one, check here:
[http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)

---

### Post by pko76 on 2011-12-19
> **BC59 said:**
> In that case you have to uninstall the old driver and install the new one, check here:
[http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04](http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04)i follow the instructions from the topic i get an error message from this command

```
sudo modprobe nvidia
FATAL: Module nvidia not found

```

also from the system > administration > hardware drivers i get that nvidia driver is activated but currently not in use

---

### Post by BC59 on 2011-12-19
Then uninstall the nvidia inputs

```
sudo apt-get purge nvidia*
```

try to install nvidia drivers through repository. These are 3 separate commands:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current
```

then reboot

---

### Post by pko76 on 2011-12-19
> **BC59 said:**
> Then uninstall the nvidia inputs

```
sudo apt-get purge nvidia*
```

try to install nvidia drivers through repository. These are 3 separate commands:

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current
```

then reboot

the error message of nvdia module doesn't exist anymore.the logo of ubuntu at startup doesn't appear and it appears a blank purple image.in system >administration>hardware drivers there is the same message nvidia driver is activated but not currently in use.

---

### Post by BC59 on 2011-12-19
Looks like a bug. Check here on the comments for workarounds:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207)

---

### Post by pko76 on 2011-12-20
> **BC59 said:**
> Looks like a bug. Check here on the comments for workarounds:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/772207)
from the topic i learned that if you install the latest drivers for nvidia maybe the problem disappears.So by installing the new drivers the error message "nvdia driver is activated but currently not in use " remains.another thing that i face is that  the recovery mode at the grub menu is not working.when i select it from the grub menu two lines are appearing that state that something is loading in a purple background and after that nothing else happens.i think my problem is much too complicated.
also after an update the low graphics mode error message appeared but at the last two boot-ups it disappeared.

---

### Post by BC59 on 2011-12-20
Let's see this. Uninstall NVIDIA:

```
sudo apt-get purge nvidia*
```

then blacklist the Linux Driver by editing:

```
sudo /etc/modprobe.d/blacklist.conf
``` 

add following into the end of file
vga16fb
nouveau
rivafb
nvidiafb
rivatv

after

```
sudo apt-get install nvidia-current
```

Load nvidia module by restarting and try if it doesn&#8217;t work:
```
sudo modprobe nvidia
```

and with the command:
```
sudo lsmod | grep -i nvidia
```

Finally run:
```
sudo nvidia-xconfig
```

---

