---
title: "VGA Unclaimed Card"
date: 2011-06-06
forum: Hardware
---

### Post by meitham on 2011-06-06
I have got the latest toshiba portege laptop R835-P56X that comes with intel graphics card, I have not been able to correctly install the right graphics driver, compiz is not working, here is my lspci

```
meitham@london:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
```

and here is my lshw
```
meitham@london:~$ sudo lshw -C video
[sudo] password for meitham: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:3000(size=64)
```
and xrandr output
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1280 x 720, maximum 1280 x 768
default connected 1280x720+0+0 0mm x 0mm
   1280x720        0.0* 
   1024x768        0.0  
   800x600        61.0  
   1280x768        0.0 
```
Any help would be appreciated.
M

---

