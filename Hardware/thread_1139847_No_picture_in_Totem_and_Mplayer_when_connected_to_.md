---
title: "No picture in Totem and Mplayer when connected to external display"
date: 2009-04-27
forum: Hardware
---

### Post by pdipizzo on 2009-04-27
I"m using Totem Movie Player and MPLayer in Ubuntu 8.10 to play .avi files. Everything works fine on my old Dell 1501 laptop. When I connect the laptop to my Acer LCD TV to watch a movie, everything keeps on working great except I cannot see the movie itself on the TV monitor. I see my full desktop and all other applications on the TV, including pictures, Youtube videos, MPlayer or Totem, etc,, and can play music too, but no image in the player itself, even if the movie plays normally on my laptop screen. The sounds works though. Is there an esoteric thing I need to do to make it work, or did I miss something?

Thanks for your help!

---

### Post by pdipizzo on 2009-04-29
So? No transcending solutions from one of you genius of the open source new world order?

---

### Post by Tomas_IV on 2009-11-20
Better late than not at all. ;)
I had similar problems with LCD TV connected through VGA analog output to my Presario laptop. I use XFCE based clone of Ubuntu called Linux Mint XFCE, but I suppose everything should be the similar if not the same as original Ubuntu.
First thing which partially worked for me was a monitor settings application under Gnome, which allowed me to switch off internal LCD an then the video worked on external monitor(TV) - the same thing did not work in similar tool in XFCE. What I missed was an fast way to switch between monitors and that it did not allowed to reach physical resolution of the full hd TV. I do not use it anymore, that's why i do not remember exact name of the tool, it was under the system settings in the menu. The procedure was a little complicated with need to first set the two monitors to a common resolution and then deactivate the internal one.
Then I found command-line tool xrandr, had read some docs on [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) and xrandr man page and now I have three simple scripts which can switch between these three scenarios:

[LIST]
[*]Internal LCD on with native 1280x800 resolution, external LCD(TV) off.
[*]Internal LCD off, External LCD(TV) on with native 1920x1080 res.
[*]Both LCDs on in their respective native resolutions, arranged below one another on virtual screen.
[/LIST]
Video works in all these modes, the latest one allows for the fullscreen video from vlc player appear on the external screen, everything other opens on the internal notebook LCD (similar arrangement can be used with Openoffice presentation). To achieve that, it is needed to set virtual resolution in the /etc/X11/xorg.conf to accommodate both displays one under another. So in my case i have in xorg.conf: 
```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                [B]# This should allow notebook lcd in native res + full hd tv arranged vertically
                Virtual 1920 1880[/B]
        EndSubSection
EndSection

```
The mentioned scripts are as follows:
lcd-auto
```
#!/bin/sh
# Ext. display is for xrandr	VGA-0
# Notebook display is	LVDS
xrandr --output VGA-0 --off --output LVDS --auto
xrandr | xmessage -file -

```
tv-auto
```
#!/bin/sh
xrandr --output LVDS --off --output VGA-0 --auto
xrandr | xmessage -file -

```
lcd+tv-auto
```
#!/bin/sh
xrandr --output VGA-0 --auto --output LVDS --auto --above VGA-0
xrandr | xmessage -file -

```
These scripts might work for any internal and external display combination as long as the virtual resolution is sufficient and the parameters of the monitors are correctly detected. The xmessage line is not needed, it just shows what mode was set for each display. 
Hope this might help.
T.

---

