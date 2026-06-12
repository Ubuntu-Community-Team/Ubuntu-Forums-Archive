---
title: "Screen settings are reset after reboot"
date: 2011-01-12
forum: Hardware
---

### Post by pmahlknecht on 2011-01-12
Hi,
I'm using Kubuntu 10.10 64bit with a Intel Core i3 processor and a H55 chipset and two TFT-Screens (both connected to the integrated graphics of the i3). I'm using the screens as one big desktop, which works fine, after configuring it in the Kubuntu system settings, except, that the settings are reset after a reboot (Screens are running again as clones).
How can I make the settings permanent?

b.r. Peter

---

### Post by Zorael on 2011-01-12
Have you tried making your display settings the default? In Display Settings, there's a scrolldown menu that says Save as Default. Do that, then run **kstartupconfig4** from a run box (Alt+F2). I'm not sure why it doesn't run that automatically but it seems to be necessary for the change to propagate.

Your **~/.kde/share/config/startupconfig** file should now reflect this change and contain the **xrandr** command that gets run upon session start; the command that actually changes the display layout. Example from mine after some testing;
```
***[...]***
# krandrrc Display ApplyOnStartup **[COLOR="Red"]false[/COLOR]**   # it says false because that's the default setting
krandrrc_display_applyonstartup=**"[COLOR="Green"]true[/COLOR]"**    # it only first becomes true here if you run kstartupconfig4 after setting a default in display settings
# krandrrc Display StartupCommands ''
krandrrc_display_startupcommands="[B]xrandr --output \"LVDS1\" --pos 0x0 --mode 1024x600 --refresh 60
xrandr --noprimary"[/b]                       # not sure why these are on two lines, I don't think that's intentional but might work just as well
***[...]***
```

---

### Post by pmahlknecht on 2011-01-18
Thanks for the reply.
Unfortunately I don't have that scrolldown menu with  the save as default option.

And my startupconfig hasn't the entries for krandrrc_display_applyonstartup and krandrrc_display_startupcommands. Even when I add them manually the xrandr command isn't executed.
Running kstartupconfig4 after adding the entries to startupconfig removes them. Any other suggestions?
br Peter

---

### Post by YelloEye on 2011-11-23
This worked great for me, now it only reverts during the login screen rather annoyingly.

---

