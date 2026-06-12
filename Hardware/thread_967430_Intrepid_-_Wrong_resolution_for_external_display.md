---
title: "Intrepid - Wrong resolution for external display"
date: 2008-11-02
forum: Hardware
---

### Post by d.hefft on 2008-11-02
Hello!

I have a problem with my laptop connected to an external TFT.

Here is my setup :
My laptop is a Thinkpad X60 with an integrated graphics chipset INTEL 945GM.
It is docked in an X6-docking station.
An external LCD monitor is plugged on the docking station (using the VGA connector).
The laptop's lid is generally closed (resolution 1024x768).

With this setup, the external monitor is set up by X with a 1024x768 resolution whereas the preferred one is 1280x1024.
It is not possible to choose this resolution in the drop-down-list for the external VGA in the display-settings.

When the lid is closed, the LVDS panel should be disabled and the external monitor should be set up with its preferred resolution. But that is not possible.

I would be really gratefull if somebody could help me with this.

---

### Post by bgblanch on 2008-11-13
I have the same issue but it doesn't look like there's a good fix for it.  It was working quite well for me in 8.04 but 8.10 limits me to the laptop resolution and doesn't turn off the laptop screen when I close the lid.

Dell D630, Intel 945GM, Dell 20" external monitor.

---

### Post by quanumphaze on 2008-11-19
I would also like to whinge about the way X in Intrepid handles things.

In Hardy when X starts with the external LCD (1280x1024) it will display a 1280x1024 screen though only 1280x800 was visible on the laptop LVDS (all visible on VGA). When I start up the gnome-settings-manager changes to my preference of having the LVDS off.

However in Intrepid it tries to be helpful assuming that 1024x768 projectors are the only thing people use the VGA port for. So I get 1024x768 on the LVDS and VGA. Gnome-settings-manager still seems to change it back to the last set settings though. Unfortunately XFCE doesn't do this (I wanted to try it but this is just too annoying) and when I manually run```
xrandr --output VGA --mode 1280x1024
xrandr --output LVDS --off
```
the panels and desktop crash when the LVDS is turned off.

And to make things worse is that Fn+F5 would behave like xrandr --auto in Hardy but does nothing in Intrepid.

---

### Post by David Valentine on 2008-11-28
I'm glad to see it's not just me.  When I dock my Thinkpad T61, it insists on using it's own LCD's resolution (1440x900) on my external monitor (1280x1024).  The resulting distorted image hurts to look at for long.  Nothing I could find under "screen resolution" helped.  Has a bug report been filed?

---

### Post by quanumphaze on 2008-11-28
Try xrandr -q

This should give a list of the output devices and the resolution modes available for them.
I recommend you also have a [COLOR="Red"]read of the man page[/COLOR] for it.
```
:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1600 x 1600
VGA connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     60.0     60.0* 
   1600x1024      60.2  
   1400x1050      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```
If the mode is available you can run something like
```
xrandr --output VGA --mode 1280x1024
xrandr --output LVDS --off
```

LVDS is what X calls the laptop's panel.

Unfortunately this is not saved for the next session, so if you log out it's back to 1024x768. If you can get Gnome Screen Resolution to work (or KDE's equivalent) hopefully it will be saved, which worked for me.

If you are feeling brave there are the user space config files that these programs write to. I can't help you here but you should be able to edit them manually to force your preference to be used when you log in.

David Valentine specificaly: I recommend you have a go at putting some lines in the monitor section of the xorg.conf file. There are plenty of xorg.conf examples out there if you need them.

---

### Post by angus.hendrick on 2008-12-03
I think I have a related problem.  On my Toshiba P105-S6147 with the Intel 945GM chipset and 1280x800 display, xrandr produces:

```

angus@angus-laptop:~/src$ xrandr -q
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1440 x 1440
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1360x768+0+0 (normal left inverted right x axis y axis) 367mm x 230mm
   1440x900       60.0 +
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)

```

The right resolution isn't even a choice.

---

### Post by quanumphaze on 2008-12-04
Please give the output of xrandr --verbose -q

Have a read of the man page for xrandr. In particular the --newmode and --addmode parts.

There is an example there too
[QUOTE="man xrandr"]```
EXAMPLES
       Sets  an output called LVDS to its preferred mode, and on its right put
       an output called VGA to preferred mode  of  a  screen  which  has  been
       physically rotated clockwise:
              xrandr  --output  LVDS --auto --rotate normal --pos 0x0 --output
              VGA --auto --rotate left --right-of LVDS

       Forces to use a 1024x768 mode on an output called VGA:
              xrandr --newmode "1024x768" 63.50  1024 1072 1176 1328  768  771
              775 798 -hsync +vsync
              xrandr --addmode VGA 1024x768
              xrandr --output VGA --mode 1024x768

```[/QUOTE]

Please know that I have never done this before and the results may be unusable and force you to kill X or reboot. This should be temporary and will go back to what it was after you log back in next time. I have no idea how to make it permanent through xrandr but you should be able to add lines to the xorg.conf to make it permanent.
In the worst case scenario you could damage your hardware by using bad settings. This used to happen back in the old days when the CRT monitors didn't check for a valid input signal and would take the signal that it couldn't handle and try to display it.

I suggest we try this out and see where this gets us.

My verbose line for 1280x800 is ```
  1280x800 (0x5b)   71.0MHz -HSync -VSync +preferred
        h: width  1280 start 1328 end 1360 total 1440 skew    0 clock   49.3KHz
        v: height  800 start  803 end  809 total  823           clock   59.9Hz

```
so try this for xrandr:```
xrandr --newmode "1280x800" 1280 1328 1360 1440 800 803 809 823 -hsync -vsync
xrandr --addmode LVDS 1280x800
xrandr --output LVDS --mode 1280x800
```

This is just the numbers from my setup, so it may or may not work. I have no idea what these numbers physically represent. If someone else has a working LVDS on a 945gm please post xrandr --verbose -q so I have more of a reference.

I conclude this is [COLOR="Red"]**at your own risk**[/COLOR]. I don't mean to scare you, I just don't want to be responsible for it going bad in that 1/1000 case. Please also look up some xorg.conf templates so that the 1280x800 mode can be added.

---

### Post by d.hefft on 2009-04-17
Today I got it! Now the correct resolution appears and it is set automatically.

It sounds crazy - but you have to use a VGA-cable with all 9 pins. 
In some cables one pin is missing because it has no function. Well, somehow this pin is responsible for the problem.

Try it!

---

