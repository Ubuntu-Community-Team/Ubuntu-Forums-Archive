---
title: "Couple Issues Sony Vaio Core i7, nvidia driver hw accel"
date: 2010-10-05
forum: Hardware
---

### Post by xyexz on 2010-10-05
Hi all, it's been a long time since I've done anything with Ubuntu but I've decided to come back to it after developing on Windows 7 for some time (since RC).

I'm running 10.04 64bit, here is some laptop information:
128GB OCZ SSD 
6GB RAM
GT 330M 512MB Gfx Card
2.6.32-24-generic
VPCF115FM Sony Vaio

So I've run into some small snags, the restricted nvidia drivers resulted in low graphics mode and I couldn't get any xorg.conf to work so I went to nvidia and downloaded the latest driver to install, ran fine:

brian@brian-pc:~$ glxinfo | grep "direct"
direct rendering: Yes

One snag is I can't seem to get VirtualBox to recognize the 3d card as I've got both Win 7 and Win XP virtual machines set to acceleration and dxdiag on both returns that D3D etc isn't available, (Aero won't work on Win 7 VM).

Running Starcraft 2 on wine resulted in a hell of a time because wine wasn't finding the libGL file (even with PlayOnLinux), so I had to set some ENV:
[PHP]
env LD_PRELOAD="/usr/lib32/nvidia-current/libGLcore.so.1" WINEPREFIX="/home/brian/.PlayOnLinux/wineprefix/SC2_WoL" wine C:\\Program\ Files\\StarCraft\ II\\StarCraft\ II.exe 
[/PHP]

So because I had to do this with SC2 I'm wondering if VirtualBox is having the same issues, I've googled for over 4 hours and not really finding out anything, I've thought about trying vmware player but I've found people having the same issues as well.

I've read on some threads that installing nvidia drivers the way I did (nvidia shell script) that it will cause issues like this, but if the restricted drivers don't work then what am I supposed to do?

The other snag is audio through wine doesn't work (I did set default audio both through wine and through wine with PoL SC2 context), I had to use this link to get audio to work on my laptop:
[http://ubuntuforums.org/showthread.php?t=1452089&#65279;](http://ubuntuforums.org/showthread.php?t=1452089&#65279;)

I really want to keep ubuntu (especially since I nuked my win 7 perfected install) but if I can't get these small snags figured out sadly I'll most likely have to return to M$ land.

So anyways, any help would be greatly appreciated and I'll try anything short of reformatting :D

Thanks,
Brian

---

