---
title: "[SOLVED] ATI driver issue..."
date: 2008-10-19
forum: Hardware
---

### Post by Brandon81 on 2008-10-19
Installed the ATI Linux Driver from the ATI Website... Probably was a mistake, but video and games run like @(#$. I have an x800XT so I verified it was in the supported hardware list. I followed the directions on the site. First I unchecked the video card in the Hardware Drivers section which may have been a mistake, it didn't indicate to do that but it didn't seem to make sense to leave it enabled. 

Anyway, everything went apparently smoothly, so I reboot to see the new drivers in action and now I keep booting up to low graphics mode. Something is definitely broken. 

So I go to uninstall the ATI drivers using an SH uninstall command. That apparently worked as well. Reboot, same issue, low graphics mode. 

So I check the driver in the hardware drivers window, thinking that'll just reinstall the other driver. Doesn't work. Reboot, same low gfx mode, and it has the driver check but says Not In Use. 

So I go to follow the Ubuntu installation guide for ATI found here: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

But when I go apt-install xorg-driver-fglrx, I get xorg-driver-fglrx is already the newest version. 

Please help!

EDIT: Possibly an error on my part. Just found this: [http://ubuntuforums.org/showthread.php?p=5215482](http://ubuntuforums.org/showthread.php?p=5215482) and am following the directions.

---

### Post by Brandon81 on 2008-10-19
Unfortunately that guide didn't fix my problem. 

I am in the process of running it again. Any advice?

EDIT: Followed it again, and this time I rebooted after checking the ATI option in hardware drivers and it's working so far. Going to try to reinstall the xserver-xorg-video-ati and see what happens. So, nevermind. Sorry for making the thread hastily.

---

### Post by kaginken on 2008-10-19
Here's another thread discussing this same problem that you may want to watch...hope this helps!:guitar:[http://ubuntuforums.org/showthread.php?t=952622](http://ubuntuforums.org/showthread.php?t=952622)

---

