---
title: "Best of Both Worlds: Full/UNR Hybrid Interface"
date: 2009-04-29
forum: Hardware
---

### Post by germclown on 2009-04-29
I gave Jaunty Netbook Remix a shot the day it came out, loved the look and feel of the kiosk interface, but found (as many have) that my EEE 701 gets super laggy when (but only when) the kiosk is visible. So I sadly switched to full desktop while I wait for the fix. But full desktop sucked up my screen space with 2 panels and a titlebar for the windows. much worse than the way the kiosk moved the titlebar up onto the only panel. So here's how I save space without putting up with a laggy kiosk screen.

notes: It only completely works while using Compiz. I assume you know how to add/remove panels and the stuff on them.

I - UNR-like Panel
=====
1) switch to standard desktop mode
     Preferences >> Switch Desktop Mode
2) remove the bottom panel and everything on it
3) remove the standard Apps/Places/System menu from the top panel
4) add "Main Menu" instead of "Menu Bar" This is to give your menu a much smaller footprint. Prefs/Admin are still available in the "System" submenu.
5) It's just me on this computer, so I dumped the User Switcher for a classic Shut Down button. To save even more space, I removed the date from the clock (it's still visible if you mouseover).
6) in the big space on the panel, add "Window Picker" (not "Window List" which is what's normally used). This seems to be the same applet as is used by the UNR desktop mode: full width and with the "x" on one end.

II - Remove Titlebars
=====
7) Install CCSM if you haven't (Add/Remove or Synaptic) and open it to window decoration.
8) Add "& !(state=maxvert)" to "Decoration Windows". This removes decorations (including titlebar) whenever the window is maxed.

That's basically it. Adjust to your taste. I run minimal options on compiz and use the UNR Murrine them with default Window colour so the panel buttons are like those in kiosk mode.

In an ideal world, a guru will come along and tell us how to remove maxed titlebars in Metacity for those not wanting to run Compiz all the time. (I assume Compiz uses more power than a 2d desktop, so I put up with a titlebar while roaming)

---

### Post by bigbrovar on 2009-04-29
are u using an intel graphic card? that might be responsible for the lag your are experiencing on your eee, experienced some lags too on my compaq mini 700 till i added **Option          "MigrationHeuristic" "greedy"** to the device section of my xorg.conf file to make it look like this 

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
       ** Option          "MigrationHeuristic" "greedy"**
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

After that everything went smooth and i experienced no more lag. btw am using the **00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)**

---

### Post by HankB on 2009-04-29
Thanks for sharing those tips. One of the things I like about the normal desktop is having the add ins for the top panel, like the little applet for local weather. I didn't see how they could be used with the UNR desktop. Can they be visible with your strategy?

thanks,
hank

---

### Post by bigbrovar on 2009-05-02
sure u can i know i have a couple of addins ( called applets) on my NBR. all u have to do is right click on an empty space in your gnome-panel and add any applet you want. if you dont see an emmty space you might want to create one by moving some applets to create one

---

### Post by germclown on 2009-05-04
Yeah, bigbrovar, I'm almost certain it's the same issue as others are having with Intel GFX chips. I'll give your suggestion a shot (thanks). Knowing almost nothing at the hardware level myself, though, do you know what effect the change would have on battery life and CPU/RAM performance? I've found on my previous laptop that a number of fixes that seemed to work beautifully on my desktop (since there's no battery) actually made my laptop much less power efficient (example: a tweak I needed to fix some Compiz bugs also gave me a 20% reduction in battery life for some reason).

Also, this guide is more for anyone too new, lazy, or scared to mess with config files. Panel manipulation is just basic *buntu functionality. Any week-old user should know at least the non-compiz stuff.

HankB: The panel my guide gives you is the same panel you get with a normal Ubuntu install. The actual list of applets may vary a bit between Desktop and UNR, but everything works exactly the same way and the most common ones are all there. I just added the weather one myself.

---

### Post by hughbert on 2009-09-29
> 8) Add "& !(state=maxvert)" to "Decoration Windows". This removes decorations (including titlebar) whenever the window is maxed.

Could you explain this step in more detail - should it be added to the command line in the "Windows Decoration" panel, or to a config file?

Thanks

---

