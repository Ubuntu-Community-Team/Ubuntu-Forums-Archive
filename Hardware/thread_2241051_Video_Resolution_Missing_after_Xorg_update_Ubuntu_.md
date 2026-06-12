---
title: "Video Resolution Missing after Xorg update Ubuntu Gnome 14.04"
date: 2014-08-23
forum: Hardware
---

### Post by VideoRoy on 2014-08-23
I have an Nvidia 9800GT have been using on this computer for many years with various versions of Ubuntu.  My current flavor is Ubuntu Gnome 14.04 and will probably use this LTS for a couple of years.

I run my resolution usually at 1600 x 1000 although my monitor will go to 1980 I believe.  I have been doing this for years but after an Xorg update today that came via Software updater  my resolution was reset to 1024x768.  It does not matter whether I use the Nvidia driver I have been using or the Nouveau driver I cannot see any resolution above 1360x768.  I would live with 1360x768 but every time I reboot the resolution defaults back to 1024 x 768. 

While using the Nvidia driver and using nvidia-settings, I saved to xorg.confg and when I checked /etc/X11/xorg.conf and it was correctly showing 1360 x 768 but no matter what happens it always my resolution defaults back to 1024x768 after a reboot.

I really want a higher resolution anyway and I have read through dozens of threads on how to work on this but fundamentally something broke because I have never had to do anything other than just pick the resolution from the menu and save.  I dual boot with Windows and when I boot to that partition the resolutions are all fine so I know my monitor and video card are working properly.

Anyone have trouble after a recent update?  I am trying to figure out if it was the update or something else in my setup.

---

### Post by VideoRoy on 2014-08-23
Ok, I figured out it is no longer detecting my monitor type.  I was able to setup a different cable config and got it recognize the monitor and show all the correct resolutions now and I can set them fine.  However after each reboot or logout it reverts to 1024x768.   My xorg.conf file is correct for resolution even with the "unknown" monitor but it continues to revert to 1024x768.

At this point if I could just force the resolution regardless of monitor I would be happy.  I must have run past that option somewhere but cannot seem to find it and you cannot do it from either the settings GUI or the nvidia-settings.  Those just modify the xorg.conf which is ignored on login.

---

### Post by VideoRoy on 2014-08-24
Ok, finally solved this one.  For some reason my monitor EDID could no longer be read reliably through my KVM switch worked sometimes but not always.  It has been working for years but something went wrong after the last Xorg update.

I suspected this since am more than familiar with the KVM switch and once I determined that was absolutely the problem finding the solution was pretty straight forward.

1. Cable direct to monitor
2. Extract EDID.bin file using nvidia-settings application since I have an Nvidia graphics board.
3. Copy EDID.bin to /etc/X11
4. Add the following line to xorg.conf  in the SCREEN  section.

**   Option         "CustomEDID" "CRT-0:/etc/X11/EDID.bin"**
 

Good reference material here  [ftp://download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-b.html](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-b.html)

---

