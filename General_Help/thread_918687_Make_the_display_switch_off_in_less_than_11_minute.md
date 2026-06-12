---
title: "Make the display switch off in less than 11 minutes"
date: 2008-09-13
forum: General Help
---

### Post by phil81uk on 2008-09-13
I have used the Power Management settings for my display to switch off after 11 minutes. But I'd like it to switch off after 3. But the slider in the graphical thing only goes down to 11.

Is there a config file associated to Power Management where I can manually changed it using gedit to a lower number?

Also, I notice that after a few minutes my display goes black, but still has a glow to it. Then, later, after approx 10 minutes it goes totally off with no glow. Why's that?

---

### Post by todak on 2008-09-13
When your display goes off, but is still glowing, it means the screensaver is set to display a blank screen. Then after the 11 minute mark, power management turns off the display. To change the time to turn off, go to **System> Preferences> Screensaver**. Move the slider all the way to the left or just deactivate the screensaver. Then click on **Power Management** at the bottom of the window and change the time slider.

---

### Post by Frantic225 on 2008-09-13
The slider doesn't go below 11, but I think you can set it if you edit the .conf.

---

### Post by AlesUbu123 on 2008-09-13
You could run 
```
gconf-editor
```
and go to /apps/gnome-power-manager/timeout directory and try changing the values of sleep_display_ac (or battery) keys (they are in seconds). You can also check out backlight dir and explore options there. 
Your screen backlight is probably still turned on because the monitor only blanks after a period of time but is not turned off in fact. 
I can't be more precise because I use KDE desktop, where in kpowersave I can easily set the duration of time after monitor sleeps and after what time it is powered off. 

BR!

---

### Post by alecava on 2008-09-13
There is no need to use the gconf-editor, the slider in power management is influenced by the slider in the screensaver options, if you set the slider in the screensaver to N minutes then the slider in the power management can't go down to N+1 minutes

---

### Post by phil81uk on 2008-09-13
> **alecava said:**
> There is no need to use the gconf-editor, the slider in power management is influenced by the slider in the screensaver options, if you set the slider in the screensaver to N minutes then the slider in the power management can't go down to N+1 minutes

That's it! That did it! Thanks a bunch guys!!

---

