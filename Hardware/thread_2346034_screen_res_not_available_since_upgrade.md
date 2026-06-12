---
title: "screen res not available since upgrade"
date: 2016-12-10
forum: Hardware
---

### Post by RumorsOfWar on 2016-12-10
Video driver not running?
I'm using an Nvidia 7300, after upgrading to 16.10 my monitors res is no longer available. Also most controls in the Nvida server-settings app are missing.
Software update/additional driver control says nvida driver 304 is installed (I confirmed correct for that card)
xorg.conf shows correct res (1440x900) ( xorg.conf was generated, but I don't think it's being used)
xfce4 display manager does not show 1440x900. 
dpkg -l grep linux shows:
 dpkg-query: no packages found matching linux
 ric@ric-NY545AAR-ABA-p6210y:~$ xrandr -s 1440x900
 Size 1440x900 not found in available modes
I did sudo apt purge nvidia*  then sudo ubuntu-drivers autoinstall, but I don't think the driver is running at all. No 3D working.

I've looked through similar threads with no luck.
Help!?

---

### Post by Yellow Pasque on 2016-12-10
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1634802](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1634802)

The updated version never made it into 16.10, probably because it triggers another serious bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1639180](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1639180)
[https://devtalk.nvidia.com/default/topic/968892/](https://devtalk.nvidia.com/default/topic/968892/)

For now, you're best off using the open source nouveau driver if it works for your card.

---

### Post by RumorsOfWar on 2016-12-10
Thanks Temujin
Hopefully they can fix that soon or I may go back to 14.04 :(
*edit*
Right after this post I checked for updates, installed the new kernel, and along with the open source driver it's fixed!
Thanks guys :)

---

