---
title: "ATI Mobility Radeon HD 5470, 3D Accelleration and Unity"
date: 2011-06-17
forum: Hardware
---

### Post by Geeksix on 2011-06-17
Hello Lovely Ubuntu peoples, 

I've installed Ubuntu 11.04 on my laptop (also my main PC), and the unity Ui is one of the loveliest well though out creations of a ui I've ever used :)

The installation was a breeze, and the setup accurately picked up monitor resolution, and all network hard ware (even wireless! woo!)

The issue comes about when I try to activate the ATI Propriety drivers, once I do so and reboot, Ubuntu tells me I don't meet the system requirements, and loads the classic gnome GUI sans-unity.

The main application I really want to be able to use is World of Warcraft, which won't work very well without 3D acceleration :) 

Using the standard Mesa driver (which everything works under, assuming I've killed ATI's driver) having done some digging, I find I'm getting the following error in my dmesg log file.
```

[ 3.372359] [drm] MTRR allocation failed. Graphics performance may suffer.
```

While looking into the issue I found a [forum post]("http://ubuntuforums.org/showthread.php?t=1755377"), which links to a bug, which suggests entering 

```
GRUB_CMDLINE_LINUX="enable_mtrr_cleanup mtrr_spare_reg_nr=1"
 solves the issue...
```

In /etc/default/grub. This didn't work (I checked my spelling :) ) and I ended up having to go into non-gui/terminal  of Linux, and use VI to change it back (I did of course run update-grub).

Here's all the information I think might be useful about my computer (Taken from a windows Dxdiag.exe report):

```
    

**HP Pavillion DV6**

          BIOS: Default System BIOS
          Processor: Intel(R) Core(TM) i5 CPU M 460  @ 2.53GHz 
          (4 CPUs), ~2.5GHz
          Memory: 4096MB RAM
          Available OS Memory: 3894MB RAM
          Page File: 1174MB used, 6611MB available


---------------
Display Devices
---------------
          Card name: ATI Mobility Radeon HD 5470 
       Manufacturer: ATI Technologies Inc.
          Chip type: ATI display adapter (0x68E0)
           DAC type: Internal DAC(400MHz)
     Display Memory: 2194 MB
   Dedicated Memory: 503 MB
      Shared Memory: 1690 MB
       Current Mode: 1366 x 768 (32 bit) (60Hz)


```

If you've made it this far and not fallen asleep, **thankyou!**

If you can give me some advice (I'm a techy, but I'm new to linux, so i'm not sure what other info I need to provide, ask me for the info and I will supply it :) ) I'd really really appreciate it, ubuntu is quite lovely I'd like to move to it permanently, this is really the only thing stopping me.

Mike

---

### Post by Yellow Pasque on 2011-06-17
Catalyst just doesn't work well with Unity at the moment (even the Catalyst version released a couple days ago). I have a feeling it won't work until Ubuntu 12.04 dev cycle begins, but maybe I'll be pleasantly surprised..
Of course, you can use Unity-2d or other DE's. If you go the Unity-2d route, you may want to find a PPA that offers the latest version.

I don't think WoW will work well with the open-source drivers (and if you have to use them, use the xorg-edgers PPA). This might help too: [https://lkml.org/lkml/2011/6/4/2](https://lkml.org/lkml/2011/6/4/2)

---

### Post by Geeksix on 2011-06-20
I could live happily enough if I could get the graphics driver working, and had to Live with standard gnome, or even KDE, but be able to run with 3D hardware acceleration for programs under wine..

I'll give this a go tonight, thanks for your advice, 

Mike

---

