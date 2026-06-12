---
title: "Nvidia 7600GS working  on 11.10"
date: 2013-04-07
forum: Hardware
---

### Post by kuifje09 on 2013-04-07
For those who are interested.
My nvidia 7600GS was not quite right detected by ubuntu and its drivers. Even the Nvidiadriver at synaptic did not do well.

After I installed the Nvidia driver NVIDIA-Linux-x86-304.88.run  everything looks perfect again.

xrandr -q
Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)

cat /etc/*rel*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

---

