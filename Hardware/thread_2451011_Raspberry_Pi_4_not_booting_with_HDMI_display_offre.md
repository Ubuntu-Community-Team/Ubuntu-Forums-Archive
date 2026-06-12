---
title: "Raspberry Pi 4 not booting with HDMI display off/removed - Solved"
date: 2020-09-24
forum: Hardware
---

### Post by timothylegg on 2020-09-24
I have a Raspberry Pi 4 that by default installation of Ubuntu 18.04, will not boot if the HDMI is disconnected or the display is turned off.

Raspberry Pi OS seems to have the same bug

[https://www.raspberrypi.org/forums/viewtopic.php?p=1547389](https://www.raspberrypi.org/forums/viewtopic.php?p=1547389)

On the page, a solution was posted by davidcotot "Adding hdmi_force_hotplug=1 to /boot/config.txt seems to have solved the problem. The Pi4 is running headless,".  However this is specific to Raspberry Pi OS.

I found a related article:

[https://askubuntu.com/questions/1274124/ubuntu-server-hdmi-hot-pluggable-on-a-rpi3b](https://askubuntu.com/questions/1274124/ubuntu-server-hdmi-hot-pluggable-on-a-rpi3b)

where a user added the lines to /boot/firmware/usercfg.txt

hdmi_force_hotplug=1
hdmi_group=1
hdmi_mode=16

and on a Raspberry Pi 4, this appears to correct the problem.  The Pi 4 booted at least twice with the HDMI cable unplugged during power-on.

---

