---
title: "Switching betwen laptop screen + external monitor"
date: 2008-05-26
forum: Hardware
---

### Post by bobbyi on 2008-05-26
Hi. I am running Hardy on my laptop.

Sometimes, I start up the laptop with no external monitor attached. When I do, Hardy correctly determines the resolution of my laptop screen (1680 x 1050 widescreen) and displays at that resolution.

Sometimes, I start up the laptop with an external monitor attached and the laptop case closed. When I do, Hardy correctly determines the resolution of the monitor (1600 x 1200) and displays at that resolution.

So this all good.

The problem is that if I start on the laptop screen and then later attach the monitor (or vice versa), I cannot find a way to get the resolution correct without rebooting.

I am not very knowledgeable about tweaking X configuration, so I was hoping the control panel applets in Gnome would make this work. However, the Screen Resolution applet does not help because it doesn't show the desired resolution in its list of choices (it acts as if I am still on the laptop screen). 

In order to change what resolution are available, I can use the Screen and Graphics Preferences applet to change my display type, but this change requires a reboot, so it is not useful since the resolution is correctly detected on reboot anyway.

What now?

---

### Post by HalPomeranz on 2008-05-26
xrandr is your friend.  From the command line, it allows you to switch around between the laptop display and an external monitor, change the resolution, etc-- all without rebooting.  One of the better links I've found that discusses xrandr is **[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)**

---

### Post by mbarak on 2008-05-26
here is a graphical program:
press Alt + F2, or run this command from the command line
```
gksudo displayconfig-gtk
```

---

### Post by bobbyi on 2008-05-26
mbarak, that is the "Screen and Graphics Preferences" applet that I refered to in my original post. Right now, I have started my laptop with the lid closed and a monitor attached. 

If I want to switch to the laptop screen (because I am going to unplug the monitor and take my laptop outside), when I open the screen and do xrandr -q, it only prints out info for the external monitor only and if use that graphical applet, it has the laptop screen as "Unknown" and won't let me set it above 800 x 600. unless I change the display type which requires a restart.

---

### Post by mbarak on 2008-05-26
maybe you just need to restart your X server
try ctrl+alt+backspace or
```
sudo /etc/init.d/gdm restart
```

---

