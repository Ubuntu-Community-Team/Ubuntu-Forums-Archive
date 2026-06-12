---
title: "Manually setting screen resolution from Terminal"
date: 2008-07-31
forum: Hardware
---

### Post by imageburn on 2008-07-31
OK, just got 8.04 installed, and upgraded. Previous to upgrade, only resolution choice was 800x600 or lower, rt? So after install, login page comes up correctly but after login, monitor (HP vs17) cannot read video input as it is 'non-synced', and the monitor informs me what the correct setting is. How do i use the terminal only option in login sessions choice to manually change Ubuntu's resolution to the correct one? I am posting this through a friends computer btw...

---

### Post by falcon61102 on 2008-07-31
Before trying to go through the terminal, try booting up the Failsafe option.  If you are using GRUB, the second option on the list is normally the failsafe.  That will prevent many of the startup modules from loading and you should be able to boot up with that and at least have the Gnome to work with.

As far as your original question goes, press CTRL+ALT+F1 or F2 and it should bring you to terminal only.

---

### Post by imageburn on 2008-07-31
Thanks for replying Falcon.

 The failsafe doesn't seem to work either, same result. I have found thru some kind of rare guesswork the /etc/X11/xorg.conf file which seems to have something to do with setting screen resolution; however it is very short with "Configured Monitor" or "Default" being the choice for all headings. I think this just might be the setting while terminal only access is underway.

UPDATE: I ran a 'sudo dpkg-reconfigure -phigh xserver-xorg f' command, seems to have reset the xorg.conf settings to the above description. I can log on to the vanilla 8.04 800x600 res as if nothing happened. Now if I could only edit this thing properly with the right settings w/o fouling everything up. Any good guides on this?

---

### Post by falcon61102 on 2008-07-31
If you have a nvidia card you can edit it very easily with 
```
sudo nvidia-settings
```

Otherwise you can use
```
sudo dpkg-reconfigure xserver-xorg
```
to automatically reconfigure your system back to it's defaults and then make adjustments from there.

Also once you get you xorg.conf file back to a normal state, you should be able to use the Screen Resolution app in teh Settings menu or 
```
displayconfig-gtk
```
to adjust the settings as necessary.

---

### Post by imageburn on 2008-08-01
That command setting to adjust screen and monitor type works great, I can't understand why the preferences tab insists on giving a menu of diminished choices in this version. Unfortunately the proper selection (1280x1024 @ 60hz) returns non-functional. Hardware issue I guess, but it wasn't a prob w/ earlier Ubuntu versions. I can't even pick from specific, as opposed to generic, the actual model (HP vs17; it's a flatscreen, not that old) as it isn't listed among the models I can choose from. *Sigh* 

Well, 800x600 working...

---

### Post by falcon61102 on 2008-08-01
It may be that your system is relying on the generic driver versions for your graphics and without the new drivers you may not be able to get a better resolution.  Also, check the back of you monitor for a model number because sometimes the list is very specific with model numbers.  Also, you may have to run 
```
sudo displayconfig-gtk
```
For the settings to be written to your xorg.conf file so they will be loaded each boot.

---

