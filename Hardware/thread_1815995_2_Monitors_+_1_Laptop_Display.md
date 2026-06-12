---
title: "2 Monitors + 1 Laptop Display"
date: 2011-08-01
forum: Hardware
---

### Post by anieruddha on 2011-08-01
Hi,

I am trying to have 3 display (2 monitors + 1 Laptop display). One monitor can be connected through HDMI and other monitor can connected through regular serial port. But Only either of monitor work. I can either connect HDMI or serial but not both.

How can I use 2 monitors along with my laptop?

OS : Ubuntu Lucid 64bit
Ram : 8GB
ATI Graphics Driver 1 GB.

I am using ATI drivers.

---

### Post by Metaxa on 2011-08-01
Can you please post the following outputs:


sudo lshw -C display; lsb_release -a

and 

xrandr -q


This will help in solving your problem


Metaxa

---

### Post by anieruddha on 2011-08-09
sudo lshw -C display; lsb_release -a output
> 
aniruddha@dinsolani-laptop:~$ sudo lshw -C display; lsb_release -a
[sudo] password for aniruddha: 
  *-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:31 memory:c0000000-cfffffff(prefetchable) memory:fbe20000-fbe3ffff ioport:e000(size=256) memory:fbe00000-fbe1ffff(prefetchable)
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid
aniruddha@dinsolani-laptop:~$ 


xrandr -q output
> 
aniruddha@dinsolani-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 2560 x 768, maximum 2806 x 2806
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x768       59.6 +
   1366x768       59.6*+
   1360x768       59.6  
   1280x720       59.6  
   1024x768       59.6  
   1024x600       59.6  
   800x600        59.6  
   800x480        59.6  
   640x480        59.6  
DFP1 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x768+1280+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x768       60.0*+
   1440x900       59.9 +   75.0     59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       60.0  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   1024x600       75.0     70.1     60.0  
   800x600        75.0     60.3     56.2  
   800x480        75.0     60.3     56.2  
   640x480        75.0     59.9  
aniruddha@dinsolani-laptop:~$


And sorry for late reply

---

### Post by anieruddha on 2011-08-16
any solution??

---

