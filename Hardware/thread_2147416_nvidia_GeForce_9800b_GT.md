---
title: "nvidia GeForce 9800b GT"
date: 2013-05-21
forum: Hardware
---

### Post by BonRouge on 2013-05-21
Hello there.

I've had this same problem for ages. Maybe someone can help...

I have this graphics card: nvidia GeForce 9800b GT.  

I've done this to install drivers: [http://linuxg.net/how-to-install-nvidia-geforce-drivers-on-ubuntu-13-04-12-10-12-04-by-ppa/](http://linuxg.net/how-to-install-nvidia-geforce-drivers-on-ubuntu-13-04-12-10-12-04-by-ppa/)  .  

I go to the nvidia system settings and I get this message: "You do not appear to using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server." I do this and try the settings thing again, but I get the same message.

It's frustrating.  I have this big monitor, but there's a big black border around my screen, and the resolution is much lower than the monitor is capable of.

I searched and found a similar problem from five years ago ([http://ubuntuforums.org/showthread.php?t=993652](http://ubuntuforums.org/showthread.php?t=993652)) but I don't think the poster's problem was resolved.

I hope someone can help.

Thanks in advance.

---

### Post by oldfred on 2013-05-22
Years ago I had issues with the drivers directly from nVidia, so I only install the versions the are in the repository. I have a 9600GT and the nVidia driver works just fine for me.

       # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

   # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

   # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by BonRouge on 2013-05-23
Thanks oldfred.  I've done those things and I'm in the same situation...  

I'm trying to fix the problem with xrandr, but having no luck.  I've tried editing the xorg.config file, but that did nothing.  In the 'Display' bit of the system settings, it identifies my monitor as 'default' and shows the resolution as 1280x1024.  There are lower options too, but this monitor is capable of 1920x1080.  It's not even the resolution itself which is the thing that bothers me about it though. It's the fact that it's a 27 inch monitor but Ubuntu sits in the middle of the screen like it thinks the monitor is about 23 inches or something like that.  I know the monitor itself is fine because Windows uses the whole screen like it should.  

Thanks for any further help.

---

