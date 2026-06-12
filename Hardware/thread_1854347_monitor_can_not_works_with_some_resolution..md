---
title: "monitor can not works with some resolution."
date: 2011-10-04
forum: Hardware
---

### Post by eexpress on 2011-10-04
```
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid
```

My LED monitor is AOC TFT22W90PS1, best resolution is 1920x1080. It works well after add two lines in xorg.conf.
	HorizSync       30.0 - 70.0
	VertRefresh     50.0 - 160.0

but monitor can not display most normally resolution: 1024x768, 800x600, 640x480, almost all other list by xrandr can work. this is too bad when i want run some windows games launched by wine, for most of those games perhaps need three resolutions above as default. and winecfg seems can not save settings, so i can not use "emulate a virtual desktop".
btw: too sad, nvidia still not support xrandr. 

part lshw info:
 ```
          *-display
                description: VGA compatible controller
                product: GT215 [GeForce GT 240]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:ce000000-cfffffff(prefetchable) ioport:dc00(size=128) memory:fbe80000-fbefffff(prefetchable)

```

```
&#9679; xrandr
Screen 0: minimum 320 x 175, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080      50.0* 
   1024x768       51.0     64.0     65.0     66.0     67.0     95.0  
   1680x1050      52.0     53.0  
   1440x900       54.0  
   1400x1050      55.0  
   1360x768       56.0     57.0  
   1280x1024      58.0  
   1280x960       59.0  
   1152x864       60.0     61.0     62.0     63.0  
   960x540        68.0  
   840x525        69.0     70.0  
   832x624        71.0  
   800x600        72.0     73.0     74.0     75.0     76.0  
   720x450        77.0  
   720x400        78.0  
   700x525        79.0  
   680x384        80.0     81.0  
   640x480        82.0     83.0     84.0     85.0  
   640x400        86.0  
   640x350        87.0  
   512x384        88.0     89.0     90.0  
   400x300        91.0  
   320x240        92.0     93.0  
   320x175        94.0  

```

---

### Post by eexpress on 2011-10-04
now i can only do it use this script, all games dock to left-up corner of screen. 

```
&#9679; cat wine.sh 
r=`xrandr|grep -o '.*\*'|cut -d' ' -f 4`
echo $r
d=`dirname "$1"`
echo $d
cd "$d"
e=`basename "$1"`
wine explorer /desktop=foo,$r "$e"

```

---

