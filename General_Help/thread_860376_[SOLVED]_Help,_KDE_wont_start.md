---
title: "[SOLVED] Help, KDE wont start"
date: 2008-07-15
forum: General Help
---

### Post by Chris Musampa on 2008-07-15
Hi all, I installed installed nvidia-settings on my pc (kubuntu gutsy) so i could sort alter brightness and contrastfor mythtv. It seemed to work ok but I fired up the machine this evening and after a 'desktop login' message flashing on the screen a couple of times it just went blank.

I can ssh the box but have no idea what to do.

Thanks in advance.

---

### Post by NikoC on 2008-07-15
+1
Have the same problem with my Geforce 6200 go series...
Installed the driver (via repos or nvidia.com) fired up kde (4) and everything worked. Rebooted and desktop environment could not start, just as you described with the screen blinking a couple of times...

Uninstalled the driver, chose "nv" instead and everything works again... tried re-installing the nvidia drivers a couple of times and the same problem persisted: as long as you don't reboot all works fine which is fairly annoying. Haven't found a solution yet ...

---

### Post by Chris Musampa on 2008-07-15
NikoC I've been using the driver with no problems for a while, it was just the nvidia settings I installed last night.

What terminal commands did you use to sort the problem?

---

### Post by NikoC on 2008-07-15
Well I didn't really sort things out, I just stopped using the nvidia driver...

Via command line make a backup of your xorg.conf
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup2
sudo nano /etc/X11/xorg.conf
Find the section "Device" and replace Driver "nvidia" by Driver "nv" (just delete -idia :)).
Ctrl + x
y
Enter

sudo /etc/init.d/kdm restart (assuming that you are using kde 3x here)
in case of kde 4x:
sudo /etc/init.d/kdm-kde4 restart

Good luck!

---

### Post by Chris Musampa on 2008-07-15
In the mean time I found this [http://ubuntuforums.org/showthread.php?t=304845](http://ubuntuforums.org/showthread.php?t=304845),  but your previous post got me started so thanks.

---

### Post by NikoC on 2008-07-16
I would just like to mention that after yesterday's updates (15th July) and reinstallation of the nvidia drivers (via restricted hardware drivers) all seems to be working well now, even after reboot and/or shutdown...

---

