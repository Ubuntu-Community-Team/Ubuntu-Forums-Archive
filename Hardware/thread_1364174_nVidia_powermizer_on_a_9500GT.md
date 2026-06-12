---
title: "nVidia powermizer on a 9500GT?"
date: 2009-12-25
forum: Hardware
---

### Post by W3ird_N3rd on 2009-12-25
I have a Geforce 9500GT PCI-e card and installed the 195 drivers from ppa:nvidia-vdpau/ppa. All would seem well, 3D seems to work, but I can't get Powermizer to work.

There are no options whatsoever in nvidia-settings. All I see is that when looking at my desktop (I'm not using special effects) it runs in Desktop performance mode, and when running something 3D is runs in Maximum performance mode.

But both modes are the same: 550Mhz GPU/400Mhz memory. "nvidia-settings -q GPUPerfModes -t" gives me only one line: "perf=0, nvclock=550, memclock=400".

Does my card seriously have no support whatsoever for Powermizer? Forum posts I've found with Google suggest my card should support Powermizer so it makes no sense to me.

---

### Post by 0nelove on 2010-01-17
With Karmic, 195.30, and a 9800GT, I get the same result: not able to use powermizer options by editing the xorg.conf. Similarly, it seems there is only one mode reported by the card to nvidia-settings:

```
~$ nvidia-settings -q GPUPerfModes -t
perf=0, nvclock=550, memclock=900
```

BUT, nvclock lists 2 modes (not just one as reported above by nvidia-settings)
```
$ nvclock -i
-- VideoBios information --
Version: 62.92.63.00.00
Signon message: NVIDIA GeForce 9800 GT VGA BIOS V2376
[B]Performance level 0: gpu 300MHz/shader 600MHz/memory 100MHz/1.00V/100%
Performance level 1: gpu 550MHz/shader 1375MHz/memory 900MHz/1.05V/100%
[/B]VID mask: 3
Voltage level 0: 0.95V, VID: 0
Voltage level 1: 1.00V, VID: 1
Voltage level 2: 1.05V, VID: 2
Voltage level 3: 1.10V, VID: 3
```

So, how to access the 2 performance levels reported by nvclock?  Have done a lot of fiddling with xorg.conf, but no success yet...  Any suggestions welcome.  subscribed - thanks.

---

### Post by Cato2 on 2010-03-19
Try a 180.x series driver.   I'm just trying to fix this by using 180.44 from nvidia.com, based on this excellent article: [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html) - explains that the 180.60 or earlier drivers give full manual control.

---

### Post by 0nelove on 2010-03-19
> **Cato2 said:**
> Try a 180.x series driver.   I'm just trying to fix this by using 180.44 from nvidia.com, based on this excellent article: [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html) - explains that the 180.60 or earlier drivers give full manual control.

Thanks Cato2!  Reading now.  Interesting.

---

### Post by Cato2 on 2010-03-20
I'm still trying to get this working - on the 180.44 driver I'm getting a flickering on the screen, which happens when the driver goes into lowest-power mode (100 MHz clock).  You can see the current performance level using ```
 nvidia-settings -q all | grep Perf
``` - the GPUCurrentPerfLevel correlates with the flickering for me.

Seems like the best option for me is to use 180.44 drivers and xorg.conf tweaks.  When I was using the 195.x drivers, I did have a GUI control for PowerMizer in the nvidia-settings tool, but I had other problems with corrupt rendering in Half-Life 2 under WINE.  However that might be worth trying.

It's best to use the nvidia.com driver download archive, as that has the widest choice of drivers - I found that Envy only suggested rather old drivers.  Although using an older driver is looking attractive now...

---

### Post by Cato2 on 2010-03-20
I've now reverted to 185.18.14 driver from Nvidia.com - this removes the flickering when at lowest PowerMizer performance level at least.

It also cures a problem introduced with the 180.44 driver: the Alt-Tab keyboard shortcut was not working in GNOME (though it did work in LXDE), and Alt-F2 was also broken - another symptom is that the Keyboard Shortcuts applet in System | Preferences menu didn't have a Window Management section which is where these would appear.

---

