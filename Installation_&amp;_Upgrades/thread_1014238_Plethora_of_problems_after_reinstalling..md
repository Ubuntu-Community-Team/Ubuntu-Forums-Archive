---
title: "Plethora of problems after reinstalling."
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by Bulletbeast on 2008-12-17
Okay, after not being able to find a fix for my problem for almost a week (and a bloody week it was), I reinstalled Intrepid. I currently have no mouse (I've edited xorg.conf into giving me at least the keyboard), no network or sound (or maybe they're just disabled, I have no mouse to click on their tray icons and see), and themes still don't work right, with gnome-appearance-manager freezing when changing themes, and them not looking right, anyway. Please, help me.

---

### Post by Bulletbeast on 2008-12-18
Bump.

---

### Post by Bulletbeast on 2008-12-18
Tried removing all input settings from xorg.conf and using .fdi files, with no success. Can anyone give me either a working xorg.conf or HAL .fdis for a generic keyboard and mouse?

---

### Post by tommcd on 2008-12-18
For the mouse, see this from the Intrepid release notes:
> 
X.Org Input Devices.
The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse 
and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from 
/etc/default/console-setup; to change them please use 
sudo dpkg-reconfigure console-setup. 
After that, HAL and X need to be restarted (e.g., by rebooting your system). 
Try that.

For the network, try running **lspci -v | grep -i eth** to list your ethernet card. Then run **lsmod** to see if the drivers are loaded, then run **sudo ifconfig** to see if eth0 is up. If all those check out ok, run **sudo dhclient eth0**. Also post your /etc/network/interfaces file.

For sound, work you way through this troubleshooting guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Is this a Wubi install or a real install?

---

