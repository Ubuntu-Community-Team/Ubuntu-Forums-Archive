---
title: "Configuring Xorg for dual screen, single wacom"
date: 2010-04-24
forum: Hardware
---

### Post by Don_Dragon on 2010-04-24
Hi, I've recently installed 10.04 on a dual screen machine.  I use Twinview Via Nvidia drivers to stretch a single desktop across both monitors.  As a result, drawing in GIMP becomes very difficult, as proportions are likewise stretched out.  Under windows, I would simply configure the tablet and restrict it to a single monitor.  But under Ubuntu 10.04, this has proven quite challenging.  I've studied the question, and the obvious solution is to add the ScreenNo option to Xorg.conf.  The problem is, Xorg.conf now seems a dated concept, no file being present by default under 10.04.

I've tried to generate one using sudo Xorg -configure, but end up with:

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


According to:

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

I can simply write a simple xorg.conf file and Xorg will apply my script to the WACOM when loading.  Trouble is, the one I've written up seems to be completely ignored.  I'm rather inexperienced with xorg.conf, so perhaps I'm missing something in the file itself.  Any advice?

Thanks for any possible insight.  Here's the .Conf file's content so far:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "stylus"
  Option        "Tilt"          "on"
  Option        "USB"           "on"                  # USB ONLY
  Option        "Twinview"      "horizontal"
  Option     "ScreenNo" "0"

EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "eraser"
  Option        "Tilt"          "on"
  Option        "USB"           "on"                  # USB ONLY
  Option        "Twinview"      "horizontal"
  Option     "ScreenNo" "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "Twinview"      "horizontal"
  Option     "ScreenNo" "0"
EndSection

# This section is for Intuos3, CintiqV5, Graphire4, or Bamboo without touch
Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

```

---

### Post by Fir3chi3f on 2010-04-25
Just to be sure, do you have the right file path? should be:
```
/etc/X11/xorg.conf
```

Made my own xorg also, and learned the hard way that the 'x' does need to be capitalized. :redface:

---

### Post by jocko on 2010-04-25
Not sure what you mean when you say the proportions are stretched? With twinview both your screens should run at their native resolutions, and any program you run should still be at the normal proportions...

Is that the entire xorg.conf?
You need more than just the InputDevice sections to get xorg to use them.
First, to generate a proper xorg.conf using the nvidia driver with twinview, run this command:
```
nvidia-xconfig -o ~/xorg.conf --force-generate --twinview --twinview-orientation="RightOf"
```This will place the new xorg.conf in your home directory so you can edit it before you move it to /etc/X11/.

I would try this simple xorg.conf first without adding any lines for the wacom device. To try it, run:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak1
sudo cp ~/xorg.conf /etc/X11/xorg.conf
```Then restart X (press Alt + Print screen + K).

If the wacom device don't work as you like it, open up the xorg.conf in your home directory, add your InputDevice sections and make sure they are used by adding the same input devices to the ServerLayout section, which should look something like this (from a link on the page you linked to):
```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen 0 "Screen0"   0 0
[COLOR=Red]#[/COLOR]        InputDevice    "Mouse0"    "CorePointer"
[COLOR=Red]#[/COLOR]        InputDevice    "Keyboard0" "CoreKeyboard"
        [COLOR=Red]InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
        InputDevice    "cursor"    "SendCoreEvents"    # For non-LCD tablets only
    InputDevice    "touch"     "SendCoreEvents"    # Only a few TabletPCs support this type
        InputDevice    "pad"   # For Intuos3/CintiqV5/Graphire4/Bamboo tablets[/COLOR]
EndSection
```Note that I don't have any wacom device, so I have no idea if you need to change anything else to get your specific device working. I have noticed that the automatic detection of mouse and keyboard works better than having a static configuration in xorg.conf, which is why I commented out the mouse and keyboard lines.

And when you have made the changes, save the file and copy it to /etc/X11 with these commands:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak2
sudo cp ~/xorg.conf /etc/X11/xorg.conf
```Then restart X (press Alt +  Print screen + K).

To go back to your original xorg.conf:
```
sudo cp /etc/X11/xorg.conf.bak1 /etc/X11/xorg.conf
```And to go back to the new one without the wacom configuration:
```
sudo cp /etc/X11/xorg.conf.bak2 /etc/X11/xorg.conf
```

---

### Post by Don_Dragon on 2010-04-25
Wow, now I'm getting somewhere... sortof.  I managed to get the Wacom to stop working, and to screw up xorg, but at least that means I'm messing with the right files now.  I've started over with a fresh xorg.conf, and I'll keep tweaking it until I get things right.

Thanks for the feedback you two, very helpful.  That's why I love Linux, the community is simply awesome.

---

### Post by habilain on 2010-04-29
Wacom tablets used to be configured via HAL FDI files, but since Lucid dropped HAL I'm not entirely sure how to set it up properly. I can provide a hacky method which lets you set up the Wacom tablet for the screen with the top left of the tablet in though, if you're using the default XOrg config. Because I'm using a Bamboo1, that's what's in my commands. You can find the appropriate string to put in by running
```
xsetwacom --list -v
```And look for the device which contains the STYLUS.

Run the following:
```
xsetwacom --get "Wacom Bamboo1" BottomX
```This gives you the X resolution of your tablet. I'll call this *TX*. Next you need the resolution of the virtual screen, which can be found by
```
xsetwacom --get "Wacom Bamboo1" SBottomX0
```I'll call this *WX*. Finally, let's call the actual X resolution of your primary screen [I]SX.
[/I]
The hacky method is to set the X resolution of your tablet to be bigger than it actually is. This effectively causes the driver to map an out-of-bounds area to your second screen. The value you should set it to, *AX* is *TX * (WX / SX)*. You might like to set it a little less than that to stop the cursor jumping to the first pixel on the second screen, but that's preference. Anyway, once you've got *AX*, set it with:
```
xsetwacom --set "Wacom Bamboo1" BottomX *AX*
```And repeat for the Y coordinates if necessary. The set commands will have to be run whenever you start using the tablet, so you might want to put them in a script. In theory it can be automated via a devicekit rule, but I've not yet got around to doing so.

---

### Post by Don_Dragon on 2010-05-06
Well, that solved my problem.  I ended up with the following two commands, one for the stylus, one for the eraser:

```
xsetwacom --set "Wacom Intuos3 6x8" BottomX 35700
xsetwacom --set "Wacom Intuos3 6x8 eraser" BottomX 35700
```

As you suggested, I messed with the numbers to remove the edge of the second monitor.  I've simply added both commands as start-up applications, and created some temporary shortcuts under system tools.  Everything works fine, but not one to be satisfied with fine, I'm going to try and write a script that toggles between single and dual screen mode, and perhaps link it to a button on my tablet, allowing me to switch modes.

Thanks

---

### Post by jomsa on 2010-05-07
[FONT=monospace]This 

[/FONT]xsetwacom --list -v
Gives me this ->
```
Unknown command '--list'
Usage: xsetwacom [options] [command [arguments...]]

```

---

### Post by Don_Dragon on 2010-05-07
What wacom are you using?

---

### Post by Favux on 2010-05-07
```
xsetwacom -v list
```

---

### Post by Cas07 on 2010-05-13
I would like to add my experience to this thread. 

I have two monitors, 1280x1024 to the left of 1920x1200. This results in a Twinview desktop of 3200x1200. 

My tablet is reported by* xsetwacom --list* as a "Wacom Volito2 4x5"

After a bit of trial and error from reading this thread, I realised using the Screen_No parameter alters the calculation. I have created a revised formula that works for my setup:

WX = Twinview Desktop X value
SX = Monitor X value
TX = Tablet X value (from xsetwacom --get "Wacom ..." BottomX)

```

Values to use Screen 0: 
TopX = 0
BottomX = TX - ( ( TX*(WX/SX) ) / 2 )

Values to use Screen 1: 
TopX = TX - ( ( TX*(WX/SX) ) / 2 )
BottomX = TX

```

This results in the following xsetwacom parameters to have the tablet  track solely across my 1920x1200 monitor:

```

xsetwacom --set "Wacom Volito2 4x5" Twinview Horizontal
xsetwacom --set "Wacom Volito2 4x5" Screen_No 1
xsetwacom --set "Wacom Volito2 4x5" TopX 851
xsetwacom --set "Wacom Volito2 4x5" BottomX 5104

```

---

### Post by osarusan on 2010-06-02
Habilain, thank you so much for this equation!

I used to use TwinView with my 2 monitors, but recently switched to an ATI card, and it was hell trying to figure out how to do this without TwinView. (I remember having lots of difficulty WITH TwinView too, actually.)

All I needed was how to figure out the number to set BottomX at, and by trail-and-error I got pretty close. But your solution there got me exactly to where I want to go, and now I've got my Wacom working properly on my non-nVidia dual monitor setup.

Major kudos to you!


> **habilain said:**
> Wacom tablets used to be configured via HAL FDI files, but since Lucid dropped HAL I'm not entirely sure how to set it up properly. I can provide a hacky method which lets you set up the Wacom tablet for the screen with the top left of the tablet in though, if you're using the default XOrg config. Because I'm using a Bamboo1, that's what's in my commands. You can find the appropriate string to put in by running
```
xsetwacom --list -v
```And look for the device which contains the STYLUS.

Run the following:
```
xsetwacom --get "Wacom Bamboo1" BottomX
```This gives you the X resolution of your tablet. I'll call this *TX*. Next you need the resolution of the virtual screen, which can be found by
```
xsetwacom --get "Wacom Bamboo1" SBottomX0
```I'll call this *WX*. Finally, let's call the actual X resolution of your primary screen [I]SX.
[/I]
The hacky method is to set the X resolution of your tablet to be bigger than it actually is. This effectively causes the driver to map an out-of-bounds area to your second screen. The value you should set it to, *AX* is *TX * (WX / SX)*. You might like to set it a little less than that to stop the cursor jumping to the first pixel on the second screen, but that's preference. Anyway, once you've got *AX*, set it with:
```
xsetwacom --set "Wacom Bamboo1" BottomX *AX*
```And repeat for the Y coordinates if necessary. The set commands will have to be run whenever you start using the tablet, so you might want to put them in a script. In theory it can be automated via a devicekit rule, but I've not yet got around to doing so.

---

### Post by jspatrick on 2010-06-20
Hey guys,

I know this thread is a little old, but...

I'm pretty new to Ubunutu and Linux, and was struggling with these screen mapping issues as well.  Thanks to the posts here, I was able to get my tablet mappings the way I wanted, but I needed a faster way to switch these around, so I wrote a little Python program to do it for me.

so I just put wacomtoggle.py in at ~/bin/wacomtoggle.py
I have the following in my ~/.bash_profile:
```
PATH=$PATH:$HOME/bin:.
```
then I need to make sure it's executable:
```
chmod ugo+x wacomtoggle.py
```
now I can do this to toggle and maintain square proportions:
```
wacomtoggle.py -p 
```

So now my main question...is there a way to map these commands to the buttons on the device itself?

Unforunately, I have to modify the values in the script for the monitor sizes and the wacom tablet sizes by hand, so some secondary questions to make the script more automagic:

- Is there a command to query the default BottomX size, even after it's been set?
- Is there a way to query monitor sizes?

If anyone has suggestions for the script feel free to share!

---

### Post by C.S.Cameron on 2010-06-20
> **Don_Dragon said:**
> but not one to be satisfied with fine, I'm going to try and write a script that toggles between single and dual screen mode, and perhaps link it to a button on my tablet, allowing me to switch modes.
Thanks

If you are still following this post you might be interested in "switchconf" from the repositories.
It allows you to switch between system configuration sets.

---

### Post by Favux on 2010-06-20
Hi jspatrick,

For bottomX use:
```
xsetwacom get stylus BottomX
```
Using whatever "Device name" or ID # 'xinput --list' gives you for stylus.  From:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

I don't know about monitor sizes, I don't think xsetwacom does that.  Maybe xrander?
```
xrandr -q --verbose | grep Screen
```

You should be able to bind the script to a pad button like I do in [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") for the Bamboo P&T.

---

### Post by blady_pirat on 2010-09-16
My scenerio:
0 - laptop display 1280x800px (left of)
1 - external LCD 1920x1200px
RandR virtual resolution - 3200x1200px
Tablet - Wacom Graphire4 4x5 (with resolution 10280x7424)
Inspired by habilain's post tried his solution - it works well, but I wanted something different. 
I wanted to restrict Wacom Tablet to the external display. I managed to accomplish that. 

First of all:
```
 xsetwacom set "NameOfTablet" TopX XX
``` takes **negative values!** 

The equation for getting TopX parameter would be:
TopX = TX - (TX*(WX/RX)
where:
TX = *Wacom horizontal resolution*
WX = *Virtual Randr horizontal resolution*
RX = *Physical right display resolution*
in my case:
TopX = 10280 - (10280*(3200/1920) = -6853
```
xsetwacom set "Wacom Graphire4 4x5" TopX -6853
```
I needed also to fix a bit BottomX value by hand (it shouldn't happen but it did)

One more thing in Ubuntu/Kubuntu 10.04 settings which normally would go into xorg.conf should go:
```
/usr/lib/X11/xorg.conf.d/10-wacom.conf
```

---

