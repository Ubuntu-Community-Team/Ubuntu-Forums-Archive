---
title: "[SOLVED] Dell won't reconfigure video"
date: 2008-08-13
forum: Hardware
---

### Post by drc330 on 2008-08-13
I'm new to Linux in general and Ubuntu specifically although I have a lot of experience with NT/XP/Vista.

I'm trying to revive a laptop for my daughter.  It's a Dell Latitude C600.  I'm having trouble getting the resolution above 800x600.  The video card is an ATI Rage Mobility 128.  I'm using the latest version of Ubuntu downloaded just last week.

I've tried copying code from these forums into the xorg.conf and the resolution does change to 1024x768 but the video is corrupted into a split screen effect.

I've also tried to reconfigure the video using  sudo dpkg-reconfigure xserver-xorg but the configurator bails out after going through the keyboard screens.

If I boot with a SUSE live CD, I can use higher resolutions but SUSE doesn't work with my wireless.  It might with wicd though... I haven't tried that yet.  I don't want to give up on Ubuntu just yet.

Help!

---

### Post by prshah on 2008-08-13
> **drc330 said:**
> 
  It's a Dell Latitude C600.  I'm having trouble getting the resolution above 800x600.  The video card is an ATI Rage Mobility 128.  I'm using the latest version of Ubuntu downloaded just last week.


From 8.04 onwards, xorg.conf (and hence dkpg-reconfigure xserver-xorg) does not play much of a role in display card/monitor selection, except that it is there if you want to add any special settings. You should press Alt+F2, then give the command```
gksudo displayconfig-gtk
```, click on the "Graphics Card" tab, and select a suitable model from the drivers list.

Once you enable the correct driver, you can change screen resolution either in the same way as above, or you can also click System-Preferences-Screen Resolution.

---

### Post by drc330 on 2008-08-13
Thanks, that does indeed get me into the video settings!
I checked Dell's website and it turns out I don't have Rage card, I have an ATI Mobility M3 w/ 8mb.

I'll play around in the configure screen to see if something works better than the default generics.

Thanks again.

---

### Post by drc330 on 2008-08-13
I was able to leave the video card setting alone and just change the monitor to LCD 1024x768.  Rebooted and so far so good.  This is way better; 800x600 is so cartoonish.

Thank-you again... I've been struggling with this for a couple of days now.

This laptop is almost ready for my daughter now!  Linux makes it a useable computer again.

---

### Post by peakshysteria on 2008-08-13
Please mark thread as SOLVED if this is so. So that others can find the solution you have.

Alt to **sudo displayconfig-gtk** you can: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others :)

---

