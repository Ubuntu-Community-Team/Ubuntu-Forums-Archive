---
title: "Nvidia drivers and xrandr broken after apt upgrade"
date: 2014-09-21
forum: Hardware
---

### Post by Krixvar on 2014-09-21
Hi all, I ran a routine apt-get upgrade yesterday, apparently not noticing it upgraded something that affected my graphics drivers, and today I booted up to a blank screen. I tried modprobing the nvidia drivers (Something got messed up a while back and I hadn't ever had time to fix it, so I've had to run modprobe then restart lightdm before getting to the login screen), but that didn't help. I rebooted once and then got a low resolution login screen.

I tried adding resolutions via xrandr, and while I could add a mode, I couldn't set it. Additionally, any time I'd run xrandr, it says "xrandr: Failed to get size of gamma for output default" before displaying the actual command output.

I also tried different drivers -- I had nvidia-331, so I tried nvidia-304 and 331-updates from the Ubuntu repos, as well as nvidia-340 from xorg-edgers (when it didn't help I removed the repo through ppa-purge). They all behaved the same way after reboots, restarting lightdm, and running modprobe -- I'd reboot and end up at a low resolution login screen.

After spending some time on the IRC channel, I was told that I have no built modules for my current kernel. However, when I install any version of the driver, it appears to be building them okay and not throwing any errors. Someone else told me to install a driver from the nvidia website, but I decided to hold off on that as I've read it can make upgrading difficult.

Other rather strange thing is that I get "command not found" when I run nvidia-xconfig - not sure if this is related to the module not being there. 

I'm running Kubuntu 14.04 64 bit. Please let me know if there are any other details I can provide - log files, command output, etc. Thank you!

Update: Turns out I had bumblebee installed, and I'm on a desktop... If I recall I had thought I needed it when I was messing around with CUDA and never ended uninstalling it. Just leaving this here in case anyone else has the same issue!

---

