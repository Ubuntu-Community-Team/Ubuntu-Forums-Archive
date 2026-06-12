---
title: "Resolution problem"
date: 2011-06-23
forum: Hardware
---

### Post by tzeus on 2011-06-23
Ok, so i am a begginer. But i really need the help, and i am squeezed pretty hard by time.

What i want to achieve:

A ubuntu OS installed to a flash, that i can carry all the places with me.
So far .. i kinda did it ... But now some problem arose:

I use this flash drive on 2 PC's 1 or 2 virtual boxes and an old notebook.
At first all was ok, but now .. is not so ok anyomore... in the virtual box  window, even if i enter fullscreen mode, the resolution will still stay 640x480 no matter what, and in laptop same way. The worse this is that  it only occupies a quarter of screen or so.
I tried to reconfigure xorg, i deleted it and created it again but nothing seems to work.

this is what
 > sudo lshw -C display; lsb_release -a; uname -a

shows me
 ```
 *-display
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:d0000000-d7ffffff memory:dff80000-dfffffff
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.04
Release:        11.04
Codename:       natty
Linux doru-VirtualBox 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
```


and i attached the xorg.xonf.txt file so u guys can have a look at it.

i have an ati card on my main pc, and i installed the driver for it but it worked even with that before. i don't really know what other information to provide... the notebook that i use is a weird model, Gericom Hummer 26640 15.x inch screen 1360x768 default resolution

i also attached a picture to show you guys how my screen looks on my notebook. it is obviously an edited picture, but that is the effect that i get. Please help me solve this ... i have tried more than one way, even using xrandr which btw, gives me this:

```

Screen 0: minimum 320 x 200, current 640 x 480, maximum 2048 x 2048
VGA1 unknown connection (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   640x480        60.0*+   59.9  



```

This is everything i have and no solution! 

thanx in advance!


As a NEW update in the situation, i removed the aTI, drivers, and did an sudo apt-get remove xserver, and then reinstalled it. The situation stays the same...

One thing i have noticed is that when the OS is loading the loading screen is in the exact same position as the desktop is(note the picture) and this makes me believe the problem is not X related... the thing is that when i booted up in the Desktop pc, the standard resolution was 1440x900(or something) and the default resolution of my monitor is 1680x1050.


so any new ideeas ? i am really out ... 

already tried the dpkg-reconfigure with or withou -phigh, both did absolutely nothing. no error message, nothing.

---

