---
title: "Completely Remove Nvidia Drivers"
date: 2010-02-16
forum: Hardware
---

### Post by Nigggo on 2010-02-16
Hi there.
I have a huge problem with my HTPC. Yesterday nearly everything worked using XBMC on Ubuntu 9.1 minimal install except some problems with 1080i and vdpau... 
So I added the SVN PPA of XBMC and updated to a later version and while updating apt-get tried to update my NVIDIA drivers to a later version from the NVIDIA VDPAU Team PPA ... while updating an error occured and system doesnt load xbmc anymore... I tried to remove nvidia drivers an install them again but it seems not to work.
```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
sudo apt-get install nvidia-glx-195 
```
I tried it that way but it still doesnt work...
[http://pastebin.com/d3622dd4f]("http://pastebin.com/d3622dd4f")
[xorg.0.log]("http://pastebin.com/m7eabaeb5")
these are my syslog and my xorg.0.log... i hope you can help my get my system run again.... it took endless time to get it work like yesterday :(

---

### Post by dabl on 2010-02-16
At the fileystem root "/":

```
sudo rm -rf nvidia*
```

should do the trick.  Fix your repo before you try installing again.  ;)

---

### Post by Nigggo on 2010-02-16
i removed all package sources and simply removed glx then... i think there might have been packeges from different sources and different versions causing the trouble.
thx

---

