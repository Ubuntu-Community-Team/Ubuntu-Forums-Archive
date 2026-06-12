---
title: "Dual Monitors + Compiz + 12.04 = Issues"
date: 2012-06-01
forum: Hardware
---

### Post by Destructo47 on 2012-06-01
Seeing as how Compiz displays the entire desktop as a single texture, and how my setup is 2x 1440x900 (2880x900), why does it screw up my entire display when I try to use it? My video card is an ATI Radeon 9250 Pro, and the texture limit (or what xrandr reports as the limit) is 4096x4096. Currently in use right now is the VESA driver, which prints errors when trying a Compiz check:
```
nick@nick-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 12.04
 Desktop environment:   GNOME
 Graphics chip:         Advanced Micro Devices [AMD] nee ATI RV280 [Radeon 9200 PRO] (rev 01)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card. 

Check if there's an alternate (proprietary) driver available? (Y/n) n
```

My system reports that no proprietary drivers are available, and I don't want to use fglrx (last time I tried that, I had to wipe my entire HDD and install fresh), and I've heard it only allows mirrored displays.

results of xrandr:
```
nick@nick-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 2880 x 900, maximum 4096 x 4096
VGA-0 connected 1440x900+1440+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1280x1024      75.0     60.0  
   1440x900       75.0     60.1* 
   1280x960       60.0  
   1152x921       76.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-0 connected 1440x900+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1440x900       75.0*+   59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
```

As of the moment of posting, my display is using Metacity. I have completely removed Unity from my system, and am running in Gnome Classic mode. When I try using Compiz, sometimes it garbles up the screen completely, makes only half of the primary monitor viable workspace, or just doesn't display anything except a wallpaper. I might also mention that Xorg is constantly using upwards of 65% of the CPU, causing everything else to slow down. Why can't I get Compiz running without crippling display errors?

---

### Post by Destructo47 on 2012-06-02
Apparently, the card's limit is actually 2048x2048. What I don't understand is why it can't do 2880x900. Shouldn't it go by the total amount of pixels, and not simply the dimensions? Or does it have something to do with the bit depth of the GPU? Anyways, a temporary workaround was to switch the monitor configuration from a horizontal stack to a vertical stack, meaning a resolution of 1440X1800.

---

