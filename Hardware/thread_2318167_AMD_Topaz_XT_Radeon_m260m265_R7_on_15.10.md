---
title: "AMD Topaz XT Radeon m260/m265 R7 on 15.10"
date: 2016-03-23
forum: Hardware
---

### Post by Michael_Bond on 2016-03-23
Just picked up a laptop that has a AMD Topaz XT Radeon m260/m265 R7 graphics card in it. 


If i try loading ubuntu 15.10 I get the boot splash screen and then the installation screen. I start configuring it and then after about 60 seconds the screen goes black. Everything else is still working (if i hit enter i see the USB light flickering indicating access, etc ...). If i modifying the grub options to not have the splash screen I get the same result. 


It is almost like the card switches to a resolution that the monitor can't support. The monitor is a full 1080p (1920x1080). I had it booted into windows before wiping the drives to make sure everything worked. So, i don't think it is a hardware issues. 

So, i thought i would try fedora to see what it did. 

When booting the screen turns black immediately after grub and never turns back on. 


If i book up using the lower graphics option from the troubleshooting menu i can get fedora installed, and everything works fine, except i'm stuck in 800x600 (obviously). 


I changed the init to 3, created an xorg.conf with Xorg -configure, and copied it into place.


looking at lspci i get the above information about the video card. There is also a second AMD video card that, i think, drives the HDMI interface. 


I trimmed down the xorg.conf to just the named card above, and for Drivers i've tried everything I could think of:
radeon (X's logs tell me no device found)
amdgpu (i'm told AMDGPU is not available)
intel (no device found, obviously, just trying it)
vesa (no device found)




I haven't tried booting Ubuntu in a lower resolution. Wanted to ask here before wasting more time on it. 


Perhaps the AMDGPU drivers? how do you install them? I heard 16.04LTS Beta is coming out on thursday and it should have AMDGPU by default. Should i wait for it? 

Anyway ... ideas on how to get it working? 

Thanks

---

### Post by Michael_Bond on 2016-03-24
I noticed this morning that this error message is flashing by fast on boot. 


drm:amdgpu_init [amdgpu]] vgacon disables amdgpu kernel modesetting


web searching for it isn't turning up much help.

---

