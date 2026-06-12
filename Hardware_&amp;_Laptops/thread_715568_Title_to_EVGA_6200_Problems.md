---
title: "Title to EVGA 6200 Problems"
date: 2008-03-05
forum: Hardware &amp; Laptops
---

### Post by GavinJuice on 2008-03-05
Just install ubuntu, updated everything, and have been running on my onboard AGP since it wouldn't recognize my geforce 6200 when i tried top install. So i enable nvidia under the restricted drivers and set priority to the 6200 in bios, plug it in, NOW when i boot ubuntu i get past grub, but it goes to a black screen: Starting NPD Server pops up [ok], a couple more, then it stops at Running local boot scripts [ok] and i just get a cursor prompt and it doesn't move from there. I get to this same point when i run the onboard agp also. Linux is all new to me and i am utterly clueless. Any help would be very appreciated. ~Gavin

---

### Post by confused57 on 2008-03-05
> **GavinJuice said:**
> Just install ubuntu, updated everything, and have been running on my onboard AGP since it wouldn't recognize my geforce 6200 when i tried top install. So i enable nvidia under the restricted drivers and set priority to the 6200 in bios, plug it in, NOW when i boot ubuntu i get past grub, but it goes to a black screen: Starting NPD Server pops up [ok], a couple more, then it stops at Running local boot scripts [ok] and i just get a cursor prompt and it doesn't move from there. I get to this same point when i run the onboard agp also. Linux is all new to me and i am utterly clueless. Any help would be very appreciated. ~Gavin
You could try booting into recovery mode and change your video driver to "vesa":
```
cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf
```
it's an uppercase X, then (one)(one)
in your video device section change the driver from "nvidia" to "vesa"(with quotes).
To save the changes...Ctrl+x, y, enter

Then to reboot:
```
shutdown -r now
```

If you're able to boot to a gui, then open Synaptic Package Manger and delete the nvidia driver that you installed with the Restricted Drivers Manager(just do a search for nvidia in synaptic).

Then you could try Envy to install the newest Nvidia drivers:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
double-clidk on the downloaded Envy .deb file...gdebi will install it, then you should have a menu item under Applications for Envy.

---

### Post by GavinJuice on 2008-03-06
Well i followed your instructions to a T, and i get the same thing when i boot up. Cursor sits and blinks after Running local boot scripts [ok]. Any other suggestions? Thanks ~Gavin

---

### Post by confused57 on 2008-03-06
> **GavinJuice said:**
> Well i followed your instructions to a T, and i get the same thing when i boot up. Cursor sits and blinks after Running local boot scripts [ok]. Any other suggestions? Thanks ~Gavin
Boot into recovery mode & try to reconfigure your xserver:
```
dpkg-reconfigure xserver-xorg
```

---

### Post by GavinJuice on 2008-03-06
ok, so i reconfigured and that worked, i get back to a GUI with onboard agp and install ENVY. I do an automatic install nvidia and let it configure itself. Reboot and i get a black screen again. So i uninstall and i'm back to square one. Any more ideas?? Thanks ~Gavin

---

### Post by PmDematagoda on 2008-03-06
I think the old nvidia package maybe causing the problems. do this:-

1) Remove the nvidia package using:-
```
sudo apt-get purge nvidia-glx-new
```

2) Reconfigure the X-Server to it's defaults using:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then see if you can get the GUI back again. If you can get the GUI back then we can get onto installing the Nvidia driver properly.

---

### Post by GavinJuice on 2008-03-06
Well i ran the first command and there was nothing to uninstall, that would be since ENVY will uninstall old drivers, or so i read.

---

### Post by PmDematagoda on 2008-03-06
> **GavinJuice said:**
> Well i ran the first command and there was nothing to uninstall, that would be since ENVY will uninstall old drivers, or so i read.

That is fine, did you continue to the second instruction?

---

### Post by GavinJuice on 2008-03-06
yes but it was just to select a screen size.

---

### Post by PmDematagoda on 2008-03-07
Did the command work? That is what really matters.

---

