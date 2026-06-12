---
title: "Thinkpad t40 Gutsy"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by brownrl on 2007-10-19
Dear Ubuntu Makers,

Thank you so much for making Gutsy Gibbon.

In Feisty Fawn I used to have two perfectly working screens:

* Laptop Screen in 1024 x 768
* External LCD 1280x1024

Ofcourse in FeistyFawn you didn't provide a tool to make this happen so I had to hack for 3 days on google and find a way to make it work by manually editing the xorg.conf file and compiling custom radeon drivers and in general doing what so many people say is the problem with Linux, Geek-Hacking...

HOWEVER!!!!

With Gutsy you people have done an even betterJOB of completely KILLING my setup and now I am reading it is impossible with once again 'default' ati/radeon video drivers to have two screens.

Infact I am having difficulty even setting basic parameters for the main laptop screen to go 1024x768...

Thank you once again for only caring about nVidia and not doing any testing at all it seems.

This almost makes me want to switch back to Windows or to another Linux Distro. Hell at this point I might as well buy a Mac.



Regards,


PS if anyone knows the 'plain jane' way of getting dual monitors with a ThinkPad T40 Laptop, I would give you my first born.

---

### Post by teryan2006 on 2007-10-19
I'm having an identical issue with a thinkpad T41. Gutsy seems to break external LCD support on this line of notebooks. Even in vesa, the external display is stuck at the same resolution as the laptop screen itself. It appears the new GtkDisplayConfig utility is clueless at this, doesn't seems to apply any resolution changes.

---

### Post by Lil on 2007-10-19
Unfortunately it's not very well publicised that the open source 'ati' and 'radeon' drivers in the xorg.conf files no longer support dual displays via Xinerama in Gutsy.

What you need to do is use the xrandr tool now, we need a GUI for it as Screens and Devices does not configure using xrandr but using Xinerama, therefore attempts at dual screen using this will fudge things up.

Your best bet is to configure xorg.conf to use the 'radeon' driver and to boot the laptop in its basic 1024x768 32bit configuration.

Then when you've booted plug in your external display.

Open a terminal and type in:

xrandr (enter)

On that you will see that it detects the internal panel's (LVDS) capability resolution wise, and any device plugged into the VGA port (VGA-0) will also be detected.

If VGA-0 is showing resolutions up to 1280x1024 we're in business.

You need to edit your xorg.conf in one small way for this to work forever more.  In your xorg.conf find a section like this:

Section "Screen"
 Identifier &#8220;Default Screen&#8221;
 Device &#8220;ATI Technologies Inc Radeon&#8230;&#8221;
 Monitor &#8220;Generic Monitor&#8221;
 DefaultDepth 24
  SubSection &#8220;Display&#8221;
    Modes &#8220;1024×768&#8243;
  EndSubSection
EndSection

Under Modes enter:

  Virtual 2304 1280

(Where the width is the width of your two screen's max resolutions added and height is the height of the highest resolution display i.e.: (1024+1280)x1280)

The whole shebang should say:

Section "Screen"
 Identifier &#8220;Default Screen&#8221;
 Device &#8220;ATI Technologies Inc Radeon&#8230;&#8221;
 Monitor &#8220;Generic Monitor&#8221;
 DefaultDepth 24
  SubSection &#8220;Display&#8221;
    Modes &#8220;1024×768&#8243;
    **Virtual 2304 1280**
  EndSubSection
EndSection

Save and close xorg.conf

Restart the X server by logging in and out again (you might have to reboot but logging in and out should do it) and you'll never need to edit xorg.conf again. 

At the command line to keep the laptop panel (LVDS) at 1024x768 and to extend the desktop on the right with your external LCD at 1280x1024 you need to enter at the command line:

xrandr --output VGA-0 --right-of VGA-0
xrandr --output VGA-0 --mode 1280x1024

How does that work?

The only pain in the **** is that this does not survive reboots but it does work right; and it supports hot plugging etc.

You can read more on my blog here: [http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

That explains mirroring, extending, even S-video output.

What we need though is a decent robust xrandr GUI and I think I'll see if I can do something myself.

I really hope this helps as I feel your pain on Linux screen management. Now I better start on that GUI!

Vicky

---

### Post by viz_e on 2007-10-19
I have the same solution. However I wonder whether there is a way to start X with the right resolution on both monitors.

I attach my xorg.conf file, that enables the big desktop on my T43p (1400x1050) and external monitor (1280x1024). After boot, the laptop monitor has the 1280x1024 resolution. This can be corrected by "xrandr --output LVDS --auto" in a shell.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "ati"
        BusID           "PCI:1:0:0"
# accelration
        Option          "AGPMode" "4"
        Option          "EnablePageFlip" "on"
        Option          "RenderAccel" "on"
        # enable (partial) PowerPlay features
        Option          "DynamicClocks" "on"
        # use bios hot keys on thinkpad (aka fn+f7)
        Option          "BIOSHotkeys" "on"
        # enable radeon specific xinerama
#       Option          "MonitorLayout" "LVDS, VGA-0"
#        Option          "MergedFB" "true"
#        Option          "CRT2Position" "LeftOf"
#        Option          "CRT2Hsync" "50-75"
#        Option          "CRT2VRefresh" "30-82"
#        Option          "MetaModes" "1400x1050-1280x1024"
#        Option          "MergedNonRectangular" "true"
#       Option          "AddARGBGLXVisuals" "True"
#
        Option "monitor-VGA" "foo"
        Option "monitor-LVDS" "bar"

        Option "ColorTiling" "on"
        Option "AccelMethod" "XAA"
#       Option "AccelMethod" "EXA"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "foo"
        Option "PreferredMode" "1280x1024"
#       Option          "DPMS"
#       HorizSync       30-100
#       VertRefresh     50-160
EndSection

Section "Monitor"
        Identifier      "bar"
        Option "PreferredMode" "1400x1050"
        Option "RightOf" "foo"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "foo"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
#               Modes           "1400x1050" "1280x1024"
                Virtual 2680 1050
        EndSubSection
#       Option "AddARGBGLXVisuals" "True"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option          "AIGLX"         "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by Lil on 2007-10-19
I'm just testing something in the Sessions preference pane where I have added a startup item with the command:

xrandr --output LVDS --mode 800x600

Just to test if it flicks my screen mode to 800x600 on login.

If it works, it's possible this could be used as a 'kludge' basis (it's not that kludgy, it's system legal) for an extended script to set this all up on login, which could in turn be created by a GUI for XrandR... Just an idea. Bearing in mind my actual trade is web development rather than local client development!

I'll let you know what happens.

**Good news! It worked! Ok the login screen will default to what you have in your xorg.conf but once you log in, you can get a Bash script to execute a series of xrandr commands to adjust the screen setup. It's not perfect but it's a quick and dirty solution. I'm sure someone with more Linux/Gnome/X server experience will be able to improve on this! I'll work on it when I get home :) and report back here.**

Vicky

---

### Post by brownrl on 2007-10-19
Greetings Fellow IBM Thinkpad frustrated owners,

Thank you to the many whom have replied.

Infact the xrandr has proven to be helpful in somewhat solving the problem...

There exists a number of little issues,

***
Main Laptop Screen 1024x768 is actually in 1280x1024 mode although it is drawn correctly with panels and such there is this void to where the mouse can go but the screen no.


***
On the second screen I add panels for windows and quick icons at the top and bottom of the screen. When I boot down then boot up the panels are all show on the first screen until I do the xrandr command then go where they should.


I see and understand how xrandr is going to change our lives for the better eventually. However forthe time being it would have been nice to get a heads up when upgrading.


Thanks a ton to those that helped.
Regards,

---

### Post by Lil on 2007-10-19
Hiya,

To solve the laptop screen being too small you could type:

xrandr --output LVDS --mode 1024x768

or

xrandr --output LVDS --auto

See what that does for you.

At the moment it's not perfect, for example as you note if you have icons/panels on the second screen, then reboot and they all get dumped on the 'wrong' screen until you rejig xrandr again. Hence why a GUI and automatic way to configure this would be beneficial; I'm going to start work on something but progress may be painfully slow as I'm not a complete Linux guru (far from it) and all this is still pretty new to me. But I'll try.

Some heads up would indeed have been useful. I submitted a fair few bugs, feedback etc. on Launchpad in the development phase of Gutsy and I had no end of problems with Screens & Resolutions until I was finally told its used to set up Xinerama dual screen setups and that the new open source ATI drivers do not support Xinerama any longer. (Severe screen corruption issues)

Early feature lists for Gutsy omitted this tool is for configuring Xinerama dual screen setups; but later ones do note it. But of course you have to know what Xinerama is to know how that affects you, know about the open source ATI drivers dropping Xinerama support...

I'll be writing another of my guides for the T40 for Gutsy installing for sure; as there is a quirk with the Brightness on screen display no longer showing up on Fn+Home/End... Think that's do with a HAL quirk telling my T40 to use the hardware control...Another matter. Otherwise though this release looks pretty good on a ThinkPad T4x series.

Once you know that Screens & Resolutions is not much use for T4x users with a Radeon 7500 (as Radeon 9000/FireGL T4xs can use the proprietary driver which still supports Xinerama I believe.)

Vicky

---

### Post by kurrier on 2007-10-20
I was having this same issue with my T41 too after Gutsy upgrade. Kinda sucked too because my laptop LCD is dead so need the external monitor to work. I had messed around with 'xrandr' with no luck. Then I commented the "HorizSync , VertRefresh"  lines, afterwards everything works fine including all the desktop effects.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "VGAOut"
        Driver          "ati"
#        Driver          "radeon"
        BusID           "PCI:0:16:0"
#       Option          "UseFBDev"              "true"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "COLOR LCD"
        Option         "DPMS"
#       HorizSync       30.0 - 110.0
#       VertRefresh     60.0 - 160.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "COLOR LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "VGAOut"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
#       Screen          "Default Screen"
        Screen 0        "Default Screen" Absolute 0 0
        Screen 1        "External Screen" Relative "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

Hope this helps. Can edit for your wanted resolution and so on, but does work for cloned video output.

---

### Post by adlibre on 2007-10-21
I have gotten my dual head setup to work on Gutsy and I came up with a way for Gnome to remember my panel preferences.  Here's a summary of what I did.

[SIZE="2"]**The Setup**[/SIZE]

Thinkpad T42 LCD: LVDS, 1400x1050
Samsung SyncMaster 940BX LCD:  VGA-O, 1280X1024
Video Card: Mobility Radeon 9600 (using Radeon RV350 Driver)

[SIZE="2"]**xrandr**[/SIZE]

I too used to use *xinerama* with multiple screens in Feisty, but apparently that's not an option anymore.  Fortunately, *xrandr* works just as well.

I followed Vicky's informative [blog entry]("http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/").
(Warning: her post above has some important typos, so look at the blog instead.)

First I set Visual Effects to "None" under:  *System/Preferences/Appearance/Visual Effects*

This will actually change your window manager from *compiz* to *metacity* after you reboot.  See [this page]("http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710") for more info on how the window manager has changed in Gutsy.

You may not need to turn off the effects, but I found that in my case the external monitor behaves awkwardly with them on.  You can always turn them on again after you get the dual setup working.

Next I added this to the Display subsection of *xorg.conf*:
```
Virtual 2680 1050
```

After rebooting, I ran *xrandr*:
```
xrandr --output VGA-0 --right-of LVDS
```

And everything worked just fine.

[SIZE="2"]**Panel Preferences**[/SIZE]

I created two more top and bottom panels for the external screen, but Gnome kept leaving them on the Laptop LCD after reboot.  To make Gnome remember you will first have to do some experimenting.

After reboot leave the panels where they are and run this command:
```
gconftool-2 --dump /apps/panel > panel.entries
```
This will dump all of the panel settings into the file *panel.entries*.

Next, move the panels over to the new screen and run the command again with another file:
```
gconftool-2 --dump /apps/panel > panel.entries2
```
(Note: you want to change as little as possible when you move the panels over; e.g. don't move any of the icons on the panels.  Otherwise the two files will show too many settings differences, which will make things difficult  to decipher.)

Now you can compare the two files to see what has changed:
```
diff panel.entries panel.entries2
```

Here was my output:
```

5369c5369
<         <int>0</int>
---
>         <int>1</int>
5558c5558
<         <int>0</int>
---
>         <int>1</int>

```

Next open up the two files and find the line numbers where they differ -- in my case lines 5369 and 5558.  Here is my first line:
```

    <entry>
      <key>toplevels/panel_0/monitor</key>
      <schema_key>/schemas/apps/panel/toplevels/monitor</schema_key>
      <value>
        <int>0</int>
      </value>
    </entry>

```
This implies that the key difference is in: */apps/panel/toplevels/panel_0/monitor*
If it is **0** then the panel is on the Laptop monitor and if it is **1** it's on the External monitor.
Similarly, the other difference is:
*/apps/panel/toplevels/panel_2/monitor*
(In your case it may be *panel_1* or something else.)

You can experiment with changing these values by running *gconf-editor* and changing the keys manually.

Here's how to change the keys from the command line:
```
gconftool-2 --type int --set /apps/panel/toplevels/panel_0/monitor 1
```
This will change the key value to **1** and you can instantly see the results.  The "--type int" part gives the datatype of the key you are changing -- in this case an integer.

You can use "get" to see the current state of the value and confirm that it has changed:
```
gconftool-2 --get /apps/panel/toplevels/panel_0/monitor
```

Once you know what changes you want to make at startup, put them in a script called *dual.sh*:
```

#!/bin/sh
sleep 25
xrandr --output VGA-0 --right-of LVDS
gconftool-2 --type int --set /apps/panel/toplevels/panel_0/monitor 1
gconftool-2 --type int --set /apps/panel/toplevels/panel_2/monitor 1

```
And make it executable:
```
chmod +x dual.sh
```
(I'll explain the reason for the sleep command below.)

[SIZE="2"]**Getting Gnome to run the startup file**[/SIZE]

Put you script in the home directory and then go to: *System/Preferences/Sessions*.
Then add your script to *Startup Programs*.  Put the full path of the script under *Command* (e.g. */home/username/dual.sh*).

Now the reason you need the *sleep* command in the script is that apparently there is no easy way to tell Gnome the order in which startup scripts should run.  See this [bug post]("https://bugs.launchpad.net/gnome-session/+bug/32194") for details.

So the workaround is to have a long enough sleep statement to make sure that all of the programs have loaded by the time your script runs.  You may want to make your sleep statement 30 seconds or longer, depending on how fast your computer starts.  Go on the safe side and make it longer; otherwise, if the the script runs before the panels have loaded it won't work.

If anyone can think of a better way to do this, please let me know.

---

### Post by Lil on 2007-10-21
Excellent stuff there, thank you for sharing that information and your hard work.

Yes there was an absolute howler of a mistake in my xorg.conf amendment here which I have now corrected. Very sorry if this has caused you some problems; that said at least I proved BulletProof X works! :D

I have a simple script I am working on today which can be called with Fn + F7 which will cycle through LCD Only, VGA Only, LCD + VGA Mirror, LCD + VGA Extend and back to the beginning and possibly a Fn + F8 S video toggle.

Of course it can be attached to any key but Fn + F7 makes sense on a ThinkPad.

Hope I can share this with you later today.

Thanks again for your fab post Adlibre, you star! :)

Vicky

---

### Post by mve-lamb on 2007-10-21
HI i have Thinkpad T41 and I want to join your company here :), it's worthless to say that i have same problems like you with configure external monitor, projector and so on, i don't want to speak about S-video...only because of S-video I need to switch  to XP and i'm not so happy to go back to MS, but i need to..

Lil I want to test your script when it's ready, just write where can find it...

Lamb

---

### Post by Lil on 2007-10-21
Ok I've not worked to integrate the excellent work carried out by adlibre here (yet) but I have finished making a script that I am now testing. :popcorn:

[LIST]
[*]- run from the command line
[*]- or attached to Fn + F7
[/LIST]

That will switch between:

[LIST=1]
[*]- Laptop Display Only
[*]- VGA Display Only
[*]- Laptop + VGA Mirrored
[*]- Laptop Display extended onto VGA Display
[/LIST]

It's very simple and doesn't allow you to tweak the resolution but it detects the best resolution for each panel and uses that, thanks to xrandr.

I'm just testing it now but it works a charm so far Eventually I hope to create something in PyGTK so there's a GUI as well. I suppose this isn't the usual way one sets up their screens but it works well and doesn't require any knowledge from the user.

Also it won't switch the display if no VGA display is physically connected but if you have it say on VGA Output Only, then unplug it, leaving no video output, one strike of Fn + F7 sorts it back out again (assuming you attached the script to the Fn + F7 keycode.) with turning on the laptop display. :-\"

I don't know any PyGTK (not really) so a completely integrated solution might be a little while off, but if you can plonk a script in your home folder somewhere, and then use gconf-edit (bit like regedit) to add the script to the Fn + F7 keystroke, you'll be fine.

As soon as it's done I'll link to it! Hopefully this evening. :guitar:

Eventually I foresee a PyGTK based Preference panel allowing the script to be tweaked, e.g. choose the mirrored resolution, extended resolutions for example, Svideo output enabler and maybe a Gnome Panel Applet of some kind to allow for quick switching graphically.

The only downside is the settings do not survive a reboot but that's not the end of the world, as I could probably fix this too although it wouldn't be bulletproof.

---

### Post by Lil on 2007-10-21
> **mve-lamb said:**
> HI i have Thinkpad T41 and I want to join your company here :), it's worthless to say that i have same problems like you with configure external monitor, projector and so on, i don't want to speak about S-video...only because of S-video I need to switch  to XP and i'm not so happy to go back to MS, but i need to..

Lil I want to test your script when it's ready, just write where can find it...

Lamb

You can now enable Svideo output easily with Xrandr 1.2 on your T41 if you've upgraded to Gutsy (or installed Xorg 7.3/XrandR 1.2 backports on Feisty)

Boot Ubuntu/the laptop with the TV/VCR etc connected via Svideo (important)

From a terminal enter:

```
xrandr --addmode S-video 800x600
xrandr –output S-video –mode 800×600
```

You can then turn off the laptop panel with

```
xrandr --output LVDS -off
```

Only downside is that at the moment PAL support is broken but it does output 60Hz NTSC fine. Most modern PAL devices can accept a 60Hz NTSC signal in colour, some will output black and white and others will just not sync at 60hz resulting in a rolling display.

Vicky

---

### Post by Lil on 2007-10-21
Ok here it is, I've stuck it under GPLv2 so you can modify it if you want so long as you share the source too, but given it's a bash script as it stands at present... You kind of have to :) But it means we can all freely modify this.

As supplied you need to do some minor configuration such as entering the Virtual line into xorg.conf and making sure you're running the radeon driver, not ati or fglrx.

This will probably also be suitable for Intel and Nvidia users but you will need to modify the script, as will Thinkpad/Radeon users who connect their external screen on the DVI port of a dock or similar.

I've attached it to this post. this is supplied without warranty and I hold no responsibility for the usage of it, that's your own choice. But it's as non destructive as possible!

Read the README file for instructions how to use it and install. It's dead simple though, bind it to a key (I explain in the README how to bind it to Fn+F7) and let it do the work or run it from the command line.

A doddle. I appreciate this probably isn't packed as well as it could be or the script to some Bash pros will look decidedly naff, I am a bit of a basic user in these respects but it works and it's pretty efficient.

I will steadily improve this over time but I have no schedule as I have other more important things to do :)

Vicky

---

### Post by Vadi on 2007-10-21
Hi all,

I don't have the problem with any external displays (I don't have any!), and, well, everything is working even better than in Fiesty (my suspend works now!).

This is probably a greedy question, but on my T40, Radeon 7500 card, the max resolution I can get is 1024x768. But thinkwiki.org says that I can get a 1400x1050 one also (well, it says "One of the following displays:" ([click]("http://www.thinkwiki.org/wiki/Category:T40")) so I *hope* I can get that).

Does anyone know how though? I can't seem to find a way.

---

### Post by Lil on 2007-10-21
> **Vadi said:**
> Hi all,

This is probably a greedy question, but on my T40, Radeon 7500 card, the max resolution I can get is 1024x768. But thinkwiki.org says that I can get a 1400x1050 one also (well, it says "One of the following displays:" ([click]("http://www.thinkwiki.org/wiki/Category:T40")) so I *hope* I can get that).

Does anyone know how though? I can't seem to find a way.

general ThinkPad questions are best answered on [Bill Morrow's Thinkpad Forums]("http://forum.thinkpads.com") but I'm nice.

You have an XGA (1024x768) ThinkPad like me, you cannot therefore get 1400x1050 out of it. LCD's have a fixed maxium resolution. You can get a SXGA+ (1400x1050) screen for them, best bet is eBay where you will need the LCD cable and screen. They aren't cheap though but the Radeon 7500 will drive the SXGA+ screen fine; just not as fast as the actual SXGA+ supplied T4x's which came with Radeon 9000/9600s or FireGL chips in the case of the 'p' series up to and including the T42.

Not many T40s came with SXGA+, more T41 and T42s did though. Personally, I wouldn't bother as the going rate for a good SXGA+ panel can be about £120 with the cable.

Maybe look out for a T40p or T41p if you're dead set on having SXGA+. The T41p was a fantastic laptop. But I'm more than happy with my almost 5 years old (such a short time, such a wonderful time, it's aged magnificiently) T40!

---

### Post by Vadi on 2007-10-21
Ahh, okay.

Also, when I come out of suspend, I get weird little graphical glitches around certain effects. But if I change to metacity, and back to Compiz, it's fine. Do you know what can fix this? I can post a screenshot if needed.

---

### Post by viz_e on 2007-10-22
At the moment I am using the solution: start internal screen and external screen in extended desktop mode and both in 1280x1024 resolution, followed by a xrandr --output LVDS --auto.

A drawback to this (apart the fact that does not survive a restart of the X server), is that I cannot move maximized windows from one screen to the other (I could with feisty).

Any ideas?

---

### Post by chloraldo on 2007-10-22
> **Lil said:**
> As supplied you need to do some minor configuration such as entering the Virtual line into xorg.conf and making sure you're running the radeon driver, not ati or fglrx.

I'm not sure how to "make sure"... What do I have to do?

I am using a T43p which has a "ATI Mobility FireGL V3200 with 128MB".

Thanks for your help

---

### Post by cogitordi on 2007-10-22
My notebook is a T40 with a Radeon 9000 video card.  I lay waste to a perfectly good Fawn installation to use the Gibbon and I wish I had not done so. At least I had Bluetooth working nicely with the Fawn. (This misfortune is my fault, of course. I had drunk the Kool-Aid.)

IS it possible to use "Desktop Effects" with this computer and Gutsy Gibbon? If so, please tell me how you've done it, with details.

---

### Post by viz_e on 2007-10-22
> 
I'm not sure how to "make sure"... What do I have to do?

I am using a T43p which has a "ATI Mobility FireGL V3200 with 128MB".

Thanks for your help


Just check your /etc/X11/xorg.conf file. In particular, look for the line starting with "Driver".

---

### Post by Vadi on 2007-10-22
> **cogitordi said:**
> My notebook is a T40 with a Radeon 9000 video card.  I lay waste to a perfectly good Fawn installation to use the Gibbon and I wish I had not done so. At least I had Bluetooth working nicely with the Fawn. (This misfortune is my fault, of course. I had drunk the Kool-Aid.)

IS it possible to use "Desktop Effects" with this computer and Gutsy Gibbon? If so, please tell me how you've done it, with details.

You sure can - I have a radeon 7500 and it works just great.

System - preferences - appearance - visual effects. They should already be enabled by default, but if you want more customization over them (and you can do a lot!) read this very helpful blog entry ([click]("http://forlong.blogage.de/")).

Note that to get the option of "custom", you need to install the compiz config settings manager - just click here if you're on gutsy - [apt:compizconfig-settings-manager]("apt:compizconfig-settings-manager")

---

### Post by Lil on 2007-10-22
That would be the line indeed but my guess is that you won't be using the Radeon driver, most likely the fglrx one but the open source 'radeon' driver should work with the FireGL V3200 being based on the Radeon X600.

Eventually ATI's proprietary drivers will support Xrandr 1.2 but it won't be right away.

It's a shame as Xrandr makes things a lot easier, I've read some documentation today on how to configure xorg.conf to configure screens using Xrandr 1.2.

It's a pain because ATI has historically been poorly supported on Linux, but this should steadily improve now that AMD/ATI has released some source code and has committed itself to co-operating further with open source.

Here are some good pages with a ThinkPad bent explaining more about 'radeon' and 'fglrx' drivers:

[http://www.thinkwiki.org/wiki/Radeon](http://www.thinkwiki.org/wiki/Radeon)
[http://www.thinkwiki.org/wiki/Fglrx](http://www.thinkwiki.org/wiki/Fglrx)

Vicky

---

### Post by cogitordi on 2007-10-22
> **Vadi said:**
> You sure can - I have a radeon 7500 and it works just great.
System - preferences - appearance - visual effects. They should already be enabled by default,

Desktop Effects in Gutsy Gibbon are not enabled by default on my T40 and I can't enable them. The system tries to enable them then bounces back with the error message that effects cannot be enabled.

---

### Post by chloraldo on 2007-10-23
> **viz_e said:**
> Just check your /etc/X11/xorg.conf file. In particular, look for the line starting with "Driver".

Ok, sorry, I wasn't clear with my question. I know where to look, but I don't know what to do if it's wrong.

Vicky wrote:
> ...and making sure you're running the radeon driver, not ati or fglrx.
So I checked my xorg.conf and saw that it is using "ati".
So what do I have to write in there? (ATI Mobility FireGL V3200 with 128MB)

---

### Post by Lil on 2007-10-23
That's a generic ATI driver I think, which also supports the older Rage series of cards.

Try changing it to: "radeon"

Save the file (Ctrl + O in nano) and Exit (Ctrl + X in nano) and then restart Gnome with logging out and back in again.

Hopefully you'll just get back to Gnome/Ubuntu login screen as usual and you won't notice any real difference.

If Ubuntu doesn't come up and instead it says you are running in a reduced graphics mode and offers to configure the screen, then switch it back to "ati"; but I see no reason for the "radeon" driver not to work since the FireGL V3200 is based on the Radeon X600; which the "radeon" driver supports.

I know my instructions have been scant, I was just in a hurry on Sunday to get the product out there with at least some guidance, future versions should make this a lot easier I hope :) When I get chance to sit down and write them!

Vicky

---

### Post by pascalm on 2007-10-23
Hello,

After the upgrade from Feisty to Gutsy, I had the same problem as described on this  thread. Fortunately Vicky and al were sharing their thoughts with possible solutions. It helped me to find a solution to my specific case. Thanks to everyone! =D>

Here is my 2 cents, I hope it could help someone...

I have a T41 which I'm using either at customer's place (the lid or screen is then opened) or at my desk with a docking station in which case the lid is closed and the display is external (whith another resolution).

So there are 2 figures:
[LIST]
[*]the display is the internal one LVDS at 1024x768
[*]the display is the external one VGA-0 at 1280x1024
[/LIST]

The small script below is testing the lid switch state and execute the relevant xrandr commands. It is executed as soon as the session starts, just after the login:
```

#!/bin/sh
#
# Adapt the resolution according to the lid switch state
#

GREPCMD="/bin/grep"

# We test the lid switch state
$GREPCMD -q "closed" /proc/acpi/button/lid/LID/state
if [ $? -eq 0 ]; then
  # The LCD is in closed position
  xrandr --output VGA-0 --auto
  xrandr --output LVDS  --off
else
  # The LCD screen is opened
   xrandr --output LVDS --auto
   xrandr --output VGA-0 --off
fi
```

Obviously, the script can be customized to execute other commands, one can imagine to change the "--auto" parameter whith a specific resolution, etc... BTW, is it possible to execute a script after X has started but before the login process?

HTH
Pascal.

---

### Post by Lil on 2007-10-23
> **pascalm said:**
> 
Obviously, the script can be customized to execute other commands, one can imagine to change the "--auto" parameter whith a specific resolution, etc... BTW, is it possible to execute a script after X has started but before the login process?

HTH
Pascal.

Pascal,

Thanks for sharing this. I'm not sure how to run a script in between X starting and login occurring but I have read about a way to configure Xrandr in the xorg.conf. I'll work on it tonight as it's possible to configure screens using xrandr in the xorg.conf file but I need to do some testing before I share that!

In the meantime my Fn+F7 attached switching script that I linked to on the other page works an absolute treat :) Even if it doesn't survive a reboot; or affect things until the desktop is up.

Vicky

---

### Post by Lil on 2007-10-23
That's a generic ATI driver I think, which also supports the older Rage series of cards.

Try changing it to: "radeon"

Save the file (Ctrl + O in nano) and Exit (Ctrl + X in nano) and then restart Gnome with logging out and back in again.

Hopefully you'll just get back to Gnome/Ubuntu login screen as usual and you won't notice any real difference.

If Ubuntu doesn't come up and instead it says you are running in a reduced graphics mode and offers to configure the screen, then switch it back to "ati"; but I see no reason for the "radeon" driver not to work since the FireGL V3200 is based on the Radeon X600; which the "radeon" driver supports.

I know my instructions have been scant, I was just in a hurry on Sunday to get the product out there with at least some guidance, future versions should make this a lot easier I hope :) When I get chance to sit down and write them!

Vicky

---

### Post by mve-lamb on 2007-10-23
Hi Vicky,
thanks for your efforts and help!
Also and to other people here thanks guys!

Today i did some testing with your script-Vicky*nice pictures in your flkr. place*, with two different external displays, and it's working, with radeon driver in xorg.config, but i have some resolution problems with external displays, the first one was LCD 19" EIZO resolution 1280x1024, but cannot reach this resolution, and second was CRT 17" normal resolution 1024x768, but can reach far more(the resolution used from  the script was 1280x768? in mirror and same in extended mode)

Any ideas why?I have one but, I'm not so sure, my xorg.config has many places with resolution specified, how looks like your's?

This is when XGA(1024x768) internal LCD and external LCD 19" (1280x1024) is conected: full cycle of your script, with xrander after every switch. 

```
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ sudo ./output.sh 
- VGA-0 Connected but not displaying anything
+ LVDS Connected Only
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ xrandr 
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2304 x 768
VGA-0 connected 800x600+0+0 (normal left inverted right) 376mm x 301mm
   800x600@60     60.3* 
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 disconnected (normal left inverted right)
LVDS connected (normal left inverted right)
   1024x768       60.0 +   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ sudo ./output.sh 
+ VGA-0 Connected Only
+ Switch to Mirror Display
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2304 x 768
VGA-0 connected 800x600+0+0 (normal left inverted right) 376mm x 301mm
   800x600@60     60.3* 
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ sudo ./output.sh 
+ Mirrored Displays
+ Switching to Extended Desktop on VGA-0
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ xrandr 
Screen 0: minimum 320 x 200, current 1824 x 768, maximum 2304 x 768
VGA-0 connected 800x600+1024+0 (normal left inverted right) 376mm x 301mm
   800x600@60     60.3* 
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ sudo ./output.sh 
+ Extended on VGA-0
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2304 x 768
VGA-0 connected (normal left inverted right)
   800x600@60     60.3  
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$
```

Martin@ThinkPad.T41 lucky one?

---

### Post by Lil on 2007-10-23
> **mve-lamb said:**
> Hi Vicky,
thanks for your efforts and help!
Also and to other people here thanks guys!

Today i did some testing with your script-Vicky*nice pictures in your flkr. place*, with two different external displays, and it's working, with radeon driver in xorg.config, but...

Thanks :) I have lots more photos to put on Flickr, but not the time hehe...

As for your  issues, it might be a better idea to open a terminal and type in: xrandr

Copy and paste the output back here and I'll be better placed to make a judgment on what xrandr is doing in your case.

Vicky

---

### Post by mve-lamb on 2007-10-23
Very quick respond :):)
here is output from xrandr
```
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2304 x 1280
VGA-0 connected 800x600+0+0 (normal left inverted right) 376mm x 301mm
   800x600@60     60.3* 
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)


```

here is when i try to xrandr --output VGA-0 --mode 1024x768
```
$ xrandr --output VGA-0 --mode 1024x768
xrandr: cannot find mode 1024x768

```

and xrandr --output VGA-0 -auto
```
$ xrandr --output VGA-0 --auto
$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2304 x 1280
VGA-0 connected 800x600+0+0 (normal left inverted right) 376mm x 301mm
   800x600@60     60.3* 
   800x600        60.3     56.2  
   800x600@56     56.2  
   640x480@60     60.0  
   640x480        60.0  
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right)

```

Martin

---

### Post by Lil on 2007-10-23
> **mve-lamb said:**
> Very quick respond :):)
here is output from xrandr...

Ok, before we go 'nuclear' :) it appears xrandr doesn't detect your VGA panel's true abilities from looking at that output as it only finds 800x600 and 640x480.

What happens if you enter:

xrandr --addmode VGA-0 1280x1024

You might get an error saying that it can't find 1280x1024, if nothing comes back though, then try it with:

xrandr --output VGA-0 --mode 1280x1024

Let me know what happens.

Also further information to look at is your xorg.conf file in full, and also what is the output from entering in the terminal: sudo ddcprobe

(With the external LCD plugged in.)

Depending on these results will further help diagnose these issues. Sometimes a monitor can lie about the resolutions it supports, sometimes becaue the VGA cable is not fully wired; but we should get this working fine, with no problems (famous last words!!)

Vicky

---

### Post by mve-lamb on 2007-10-23
hehe, nice :guitar:, I will take you a beer, if you'd like :)
here  is output:
```
mve@mve-laptop:~$ sudo xrandr --addmode VGA-0 1280x1024
xrandr: cannot find mode "1280x1024"
mve@mve-laptop:~$ xrandr --output VGA-0 --mode 1280x1024
xrandr: cannot find mode 1280x1024
mve@mve-laptop:~$ sudo ddcprobe
vbe: VESA 2.0 detected.
oem: ATI MOBILITY RADEON 7500
memory: 32704kb
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edidfail
mve@mve-laptop:~$ 

```

I think the problem is my xorg here is:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us,bg"
	Option		"XkbVariant"	",phonetic"
	Option		"XkbOptions"	"grp:alt_shift_toggle,grp_led:scroll"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual		2304 1280
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

someone will beat me :lolflag:
I think it's a big mess, and I'm not sure but that happened after upgrade to Gusty :confused:
Martin

---

### Post by Lil on 2007-10-24
All the 'stuff' in the xorg.conf looks like the result of it being tweaked by Screen & Graphics preferences in Gutsy.

You can try backing up your xorg.conf file (e.g. cp /etc/X11/xorg.conf ~/) and then getting a clean one from scratch by entering: sudo dpkg-reconfigure -phigh xserver-xorg

Then edit /etc/X11/xorg.conf reinstating "radeon" as the driver and the Virtual line.

Log out and back in again, all being well your 1024x768 LCD comes up fine (no reason not to) and then run 'xrandr' after doing this with your VGA LCD screen plugged in again and posting the output back here. Then we'll go from there.

Vicky

---

### Post by imthemp3king on 2007-10-24
> **pascalm said:**
> Hello,

After the upgrade from Feisty to Gutsy, I had the same problem as described on this  thread. Fortunately Vicky and al were sharing their thoughts with possible solutions. It helped me to find a solution to my specific case. Thanks to everyone! =D>

Here is my 2 cents, I hope it could help someone...

I have a T41 which I'm using either at customer's place (the lid or screen is then opened) or at my desk with a docking station in which case the lid is closed and the display is external (whith another resolution).

So there are 2 figures:
[LIST]
[*]the display is the internal one LVDS at 1024x768
[*]the display is the external one VGA-0 at 1280x1024
[/LIST]

The small script below is testing the lid switch state and execute the relevant xrandr commands. It is executed as soon as the session starts, just after the login:
```

#!/bin/sh
#
# Adapt the resolution according to the lid switch state
#

GREPCMD="/bin/grep"

# We test the lid switch state
$GREPCMD -q "closed" /proc/acpi/button/lid/LID/state
if [ $? -eq 0 ]; then
  # The LCD is in closed position
  xrandr --output VGA-0 --auto
  xrandr --output LVDS  --off
else
  # The LCD screen is opened
   xrandr --output LVDS --auto
   xrandr --output VGA-0 --off
fi
```

Obviously, the script can be customized to execute other commands, one can imagine to change the "--auto" parameter whith a specific resolution, etc... BTW, is it possible to execute a script after X has started but before the login process?

HTH
Pascal.

i am still using xgl and 8.40 drivers to get my external dual display working along with my 3d effects.  The only drawback is that I have to fudge with it when I am undocked and working with just the laptop lcd because it still thinks I have 2 displays running so I only get half the display.  Sometimes apps launch and reside offscreen.  So this script interests me greatly.  Can this be run from init.d before X starts?  I would like to have it run the aticonfig commands I use since I am not using xrandr

---

### Post by mve-lamb on 2007-10-24
Vicky=Vicroty BIG THANKS, 

> **Lil said:**
> All the 'stuff' in the xorg.conf looks like the result of it being tweaked by Screen & Graphics preferences in Gutsy.

You can try backing up your xorg.conf file (e.g. cp /etc/X11/xorg.conf ~/) and then getting a clean one from scratch by entering: sudo dpkg-reconfigure -phigh xserver-xorg

Then edit /etc/X11/xorg.conf reinstating "radeon" as the driver and the Virtual line.

Log out and back in again, all being well your 1024x768 LCD comes up fine (no reason not to) and then run 'xrandr' after doing this with your VGA LCD screen plugged in again and posting the output back here. Then we'll go from there.

Vicky

I did what you told me to do, and here is result:
```
mve@mve-laptop:~/LINUX/OutputSwitcher/OUTPUT SWITCHER v.1$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2304 x 1280
VGA-0 connected (normal left inverted right)
   1280x1024      60.0 +   75.0     59.9  
   1280x960       74.9     59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)
``` :popcorn:

Thank you, your script is working very well!  Only in MIRROR Mode LVDS and external LCD together put 1024x768 on external LCD.

Virtual mode is "Virtual   2304 1280 " Using Radeon Driver!

Thank you for kindness Vicky, wonderful UBUNTU forum!  

Lamb :)

---

### Post by Lil on 2007-10-26
> **mve-lamb said:**
> Vicky=Vicroty BIG THANKS, 
Thank you, your script is working very well!  Only in MIRROR Mode LVDS and external LCD together put 1024x768 on external LCD.

Virtual mode is "Virtual   2304 1280 " Using Radeon Driver!

Thank you for kindness Vicky, wonderful UBUNTU forum!  

Lamb :)

No problem, just pleased you got it working :) Lots more to do yet but I'm getting there with some ideas! For now I'm happy to use this script on my systems as it covers me for all eventualities. I look forward to BarCamp 3 in London in November with my 'buntu laptop hooking up to projectors and displays with great ease :)

Vicky

---

### Post by Lil on 2007-10-26
Some more information for those who want to really push the boat out with this stuff.

[http://www.thinkwiki.org/wiki/How_to_configure_acpid](http://www.thinkwiki.org/wiki/How_to_configure_acpid)

This is the ACPI daemon which should be able do something when you close the lid of your laptop to detect via xrandr the presence of an external display and then if there is, switch off the display as the ACPI lid script probably already does, and then issue an xrandr command to enable the VGA-0 video output.

Or you can use my script which you can run before closing the lid and then run it again on reopening the lid; which would be pretty much what you have to do in Windows.

What I need is a seemless way for all this to work, a GUI etc... But I am getting close to having all the the technical bits in place like using xrandr in xorg.conf to configure screens, the actual detection route works pretty well... I just hope my slow progress with PyGTK etc. isn't too slow. Or of course better still is someone else does the very thing I am looking for, I am aware of Urandr but I'm not sure if that'll go far enough.

We'll see :)

Vicky

---

### Post by Vadi on 2007-10-26
By the way, since we people don't get a Windows key, here are instructions (interpreted for newsbie) from thinkwiki.org to replace it with the Caps key. This is very useful for Compiz :)

 CAPS to substitute Win/Super

Open the Terminal - Applications - Accessories - Terminal.

Copy/paste the following in it:

```
gedit ~/.Xmodmap
```

Then copy/paste the following into the text editor that comes up:

```
! No Caps Lock
clear lock
! Caps Lock as Win key
add mod4 = Caps_Lock
```

Press Ctrl+S to save it, then copy/paste this in the terminal for changes to take effect:

```
xmodmap ~/.Xmodmap
```

---

### Post by schlehmil on 2007-10-28
> **pascalm said:**
> Hello,

After the upgrade from Feisty to Gutsy, I had the same problem as described on this  thread. Fortunately Vicky and al were sharing their thoughts with possible solutions. It helped me to find a solution to my specific case. Thanks to everyone! =D>

Here is my 2 cents, I hope it could help someone...

I have a T41 which I'm using either at customer's place (the lid or screen is then opened) or at my desk with a docking station in which case the lid is closed and the display is external (whith another resolution).

So there are 2 figures:
[LIST]
[*]the display is the internal one LVDS at 1024x768
[*]the display is the external one VGA-0 at 1280x1024
[/LIST]

The small script below is testing the lid switch state and execute the relevant xrandr commands. It is executed as soon as the session starts, just after the login:
```

#!/bin/sh
#
# Adapt the resolution according to the lid switch state
#

GREPCMD="/bin/grep"

# We test the lid switch state
$GREPCMD -q "closed" /proc/acpi/button/lid/LID/state
if [ $? -eq 0 ]; then
  # The LCD is in closed position
  xrandr --output VGA-0 --auto
  xrandr --output LVDS  --off
else
  # The LCD screen is opened
   xrandr --output LVDS --auto
   xrandr --output VGA-0 --off
fi
```

Obviously, the script can be customized to execute other commands, one can imagine to change the "--auto" parameter whith a specific resolution, etc... BTW, is it possible to execute a script after X has started but before the login process?

HTH
Pascal.

To get the correct display output on gdm startup I execute this script from /etc/gdm/Init/Default.

---

### Post by caspar_wrede on 2007-10-28
Phew! What a drag this is. But thanks for the good work people.

> 
To get the correct display output on gdm startup I execute this script from /etc/gdm/Init/Default.



Any idea how to get the same effect in Kubuntu?

---

### Post by caspar_wrede on 2007-10-29
(Ping!) Help!

---

### Post by Vadi on 2007-10-30
Can anyone help me get a script working that'll do "compiz --replace" after my t40 wakes up from hibernation?

Because when it wakes up from hibernate (it's fine it from suspend), the colors are somewhat messed up. If I restart compiz though, it looks fine. But I have no idea how to go about this, I'm not into hardware much.

---

### Post by Lil on 2007-11-02
> **Vadi said:**
> Can anyone help me get a script working that'll do "compiz --replace" after my t40 wakes up from hibernation?

Because when it wakes up from hibernate (it's fine it from suspend), the colors are somewhat messed up. If I restart compiz though, it looks fine. But I have no idea how to go about this, I'm not into hardware much.

Vadi,

When I get home I'll be able to point you in the right direction but the best I can think of is placing a small script in /etc/acpi/resume.d that will be executed on any resume from suspend or hibernate to call this.

How does this sound?

Vicky

---

### Post by Vadi on 2007-11-02
I don't want it to do it from when it resumes, it resumes okay. Only from hibernate?

---

### Post by Lil on 2007-11-02
> **Vadi said:**
> I don't want it to do it from when it resumes, it resumes okay. Only from hibernate?

In which case you can do that but it would require a little more work and not having done it I can't say it would definitely work.

[LIST=1]
[*]In a terminal:
[*]```
sudo cp /etc/acpi/resume.sh /etc/acpi/resume_hibernate.sh
```
[*]```
sudo nano /etc/acpi/hibernate.sh
```
[*]At the end of the file where there is a line that says: 

```
. /etc/acpi/resume.sh
```

change it to read:
```

. /etc/acpi/resume_hibernate.sh
```

[*]Save the changes
[*]```
mkdir resume_hibernate.d
```
[*]```
sudo nano /etc/acpi/resume_hibernate.d/10-run-compiz-fix.sh
```
[*]Enter: 

```
#!/bin/bash
. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXconsole;

compiz --replace
```

[*]Save and exit
[*]```
sudo nano /etc/acpi/resume_hibernate.sh
```
[*]After the line 'done' (very end) enter beginning on a new line:

```
# Source from /etc/acpi/resume_hibernate.d/
for SCRIPT in /etc/acpi/resume_hibernate.d/*.sh; do
    if [ -x $SCRIPT ]; then
        . $SCRIPT
    fi
done
```

[*]Save and exit
[*]Done

[/LIST]

You may have to reboot for these changes to come into effect however what this does is tells the hibernate script not to use only the standard resume scripts in resume.d but also to run everything in resume_hibernate.d when you come back from hibernation.

I have not tested this but there is no reason for it not to work as it doesn't meddle with your existing resume scripts and only adds to them by adding a specific resume from hibernate scripts folder.

I cannot vouch or take responsibility for this but I have no reason to believe this will do any harm. Any quandries, ask rather than guessing :)

Vicky

---

### Post by Vadi on 2007-11-02
Hm before step 5 I had to manually go to the directory and only then do it, because otherwise it created whever I was in.

I'm a bit confused at step 11 though - do you want me to type 'beginning' after done or?

Currently, my resume_hibernate.sh has the following:

```
#!/bin/bash

# Source from /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
    if [ -x $SCRIPT ]; then
        . $SCRIPT
    fi
done


```

---

### Post by Lil on 2007-11-02
Yes step 5 you are quite right you do need to cd /etc/acpi

My doozie, I'm off to bed in a minute :)

The resume_hibernate.sh file should look like this (this is it in full):

```
#!/bin/bash

# Source from /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
    if [ -x $SCRIPT ]; then
        . $SCRIPT
    fi
done

# Source from /etc/acpi/resume_hibernate.d/
for SCRIPT in /etc/acpi/resume_hibernate.d/*.sh; do
    if [ -x $SCRIPT ]; then
        . $SCRIPT
    fi
done
```

When it looks like that, save and exit.

Basically this runs every script in resume.d first, and then runs every script in resume_hibernate.d afterwards.

This should be a good time as by then all essential services are back up and running after resume.d has run through everything; so Compiz should be ready to do its thing on the X display(s).

Sorry if this sounds 'brief' but I am so tired :)

EDIT: Oh and finally you will probably have to add root ownership and execute permissions to the script 10-run-compiz-fix.sh with:

```
sudo chown root:root /etc/acpi/resume_hibernate.d/10-run-compiz-fix.sh
```

and execute permissions:

```
sudo chmod 755 /etc/acpi/resume_hibernate.d/10-run-compiz-fix.sh
```

Vicky

---

### Post by Vadi on 2007-11-05
Okay, that sort of works.

Before, resuming from hibernate was like Ubuntu being brought back from the dead, with a lot of fancy weird graphical glitches and stuttering. But it would back, a bit ruffled though - compiz was working, but there would be odd lines here and there at window edges.

Now, it looks like it comes back, gets zapped several times (the unlock screen blinks several times), and is half-alive. My windows don't wobble, my top gnome panel bar isn't transparent, and my scale plugin doesn't work either, but AWN is working just fine for some reason (so *some* compositing is going on). But I still need to do compiz --replace manually to get compiz fully working.

Any other ideas? :/

Oh and also sometimes, randomly, it would tell me that my laptop failed to hibernate properly. Though the times that it tells me that are no different from other resumes.

---

### Post by Vadi on 2007-11-10
Whaah. Yeah, I don't like the new way, the old one without the script was better.

How can I go back please? :(

---

### Post by Lil on 2007-11-10
> **Vadi said:**
> Whaah. Yeah, I don't like the new way, the old one without the script was better.

How can I go back please? :(

Easy. Just reverse what you put into the hibernate.sh file.

In other words where you have the line:

```
. /etc/acpi/resume_hibernate.sh
```

Replace it with the original statement:

```
. /etc/acpi/resume.sh
```

In my opinion, I don't think Compiz is really read for the prime time. It's got more than its fair share of glitches on so many systems. By comparison, Mac OS X's Quartz compisitor and Vista's Aero compositing engines work a lot better at present. Maybe this will have changed when 8.04 comes along.

Vicky

---

### Post by Vadi on 2007-11-10
Maybe, except that I'm *very* positive Aero will not run on a T40.

Never experienced any glitches with Compiz either - but I'm not trying any of the "unsupported" or "alpha" plugins either, just the main ones. Scale + Expo + Group tabs = happy, efficient me. But, ymmv, Compiz is only a year old. 

Where can I see what features Aero (beside the "flip" window switcher) has?

---

### Post by Lil on 2007-11-10
> **Vadi said:**
> Maybe, except that I'm *very* positive Aero will not run on a T40.

Never experienced any glitches with Compiz either - but I'm not trying any of the "unsupported" or "alpha" plugins either, just the main ones. Scale + Expo + Group tabs = happy, efficient me. But, ymmv, Compiz is only a year old. 

Where can I see what features Aero (beside the "flip" window switcher) has?

No, the Radeon 7500 is not supported by Aero; but my point was that with regard to Aero and Mac OS X's Quartz--it appears that proportionately less people have issues with those compositors than Ubuntu users with Compiz. That's not me knocking Ubuntu and Compiz (after all I am a 100% Ubuntu/Linux user; no Windows at home) but something that is an unspoken truth that Compiz works great for some but it's still glitchy from my own tests on both ATI and Nvidia hardware.

F-Spot suffers badly, with full screen issues and also I've noticed windows minimising with artefacts on some occassions. I've found my Ubuntu experience to be more stable with Compiz/Desktop Effects disabled.

Remember Aero isn't just about 3D effects or transparency, it's the same as Quartz 2D and Compiz which move the screen rendering from a mostly CPU driven affair to something the GPU can manage; which it's more than adept at doing and will do a better job. So on the face of it Aero doesn't have as much 3D 'glitz' as Mac OS X, no where near as much as Compiz.

However, with all due respect it would seem that as a consequence of enabling Compiz you are experiencing one glitch in so far as the colours get screwed up on resume until you restart Compiz. :)

Anyway I'm not knocking Ubuntu or Compiz; I just think a fair bit more work is required to really solidify these foundations to make it seemless. Mac OS X for example when you change resolution fades smoothly out and back in without all the screen buffer jumping. It's only good to be critical of these things so that improvements come along :)

Vicky

---

### Post by Vadi on 2007-11-10
Actually, the color glitch went away - switched back to the "ati" driver which was set by default and not the "radeon" one I was using. So it was a driver issue :).
Nor I think Compiz actually handles your screen resolution either :|.

Well, I'm sure the Aero and Mac's things were buggy in the same way before they were 1.0 too, I don't think comparing a finished product to a non-finished one is logical.

Which, yes, brings to your point that Compiz isn't ready for everybody. But for those who it is, it very much is needed!

---

### Post by Vadi on 2007-11-12
Lil I need your help again :(

I used to be able to play Neverball and Warzone 2100 back on Fiesty, but on Gutsy, Neverball *completely* locks my laptop up (except for the mouse), and Warzone 2100 just kicks me back to the login screen.

I was also trying another game (Thunder&Lightning), and it completely locks the comp up also. It's author told me it must be a driver issue - but I tried on both the ati and radeon driver, same result. With compiz on/off also, same thing.

Do you know how can I downgrade my drivers back to 7.04? I'm really not liking this "upgrade".

---

### Post by PapaGoose on 2007-11-16
Hi, just thought I'd add my experience about what happened with my T40. When I plug an external 22" monitor and in boot up without any config changes, i get a 1024x768 display on the notebook LCD, and I get a 1680x1050 display on my monitor. Except that on my monitor, the size of the Gnome taskbars is still 1024x768. 

Curiously, if I then ran > xrandr --output LVDS --mode 1024x768 the monitor would also switch back to 1024x768. It seemed that the monitor was somehow tied to the resolution settings of the laptop display. Further, it was completely impossible to set the resolution in Ubuntu correctly without manually changing it in xrandr- I couldn't get the monitor modes to appear in the Screen Resolutions dialog and if I made any changes in Screens and Graphics, they usually resulted in screwing up xorg. Eventually, I ended up with the following xorg.conf
> Section "Files"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Option		"MergedFB"	"off"
	Option		"AGPSize"	"32"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050@60"	"1680x1050@75"	"1600x1024@60"	"1920x1200@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #  
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
EndSection
Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"	"640x480@72"	"640x480@75"	"800x600@56"	"800x600@72"	"800x600@75"	"800x600@60"	"832x624@75"	"1024x768@75"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1400x1050@75"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Rather messy and ugly. But if I run > xrandr --output LVDS  --off right after startup, while the monitor resolution is 1680x1050 but Gnome isn't correctly sized, then the laptop monitor turns off as normal, and Gnome automatically resizes to 1680x1050 as it should. So I used pascalm's lid-checking script to automate it, and it works perfectly (thanks!). 

Also, for anyone interested in setting up Compiz, I kept getting a maximum 3D texture size error. Obviously, it would be possible to skip the checks and start up Compiz with a script. But that wasn't to my liking. I edited /usr/bin/compiz, and where it checks for the max texture size (line 231 for me) I changed 'return 1' which fails the test to 'return 0'. With the fixed compiz script, desktop effects can be permanently enabled from the 'Appearance' menu under System > Preferences. 

On a large monitor, texture sizes could be a problem. Incidentally, Emerald seemed to work better on this chipset (ATI Radeon Mobility 7500). I'd get corruption effects if I had the colour depth set to 24, presumably since there wasn't enough memory (things like random colour pattens on half the screen etc.). Changing this to 16 fixed that problem, but it meant gradients looks rather shoddy, and I was getting problems with transparency, which wasn't working correctly. The fix was to add > Option	"AGPSize"	"32" to the Device section in xorg.conf, which correctly set the memory size for the card. This allowed me to use a depth of 24 at 1680x1050 with no problems whatsoever :) so everything is working now!

Thanks to everyone here for all the advice that got it up and running

---

### Post by Vadi on 2007-11-16
My problem was fixed, see here ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/162888](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/162888))

---

### Post by phen on 2007-11-24
thank you!

for years now i waited for the possibility to simply switch between docked and undocked operation. Either I had to use primary and secondary displays or i had to switch displays during boot.

now, with xrandr, lils tipps and pascals script, it is AT LEAST there: full docking station compatibility :-)

nearly one year ago I asked for help on that subject, and two years ago, too. see the dates of the posts :-))))))
[http://ubuntuforums.org/showthread.php?p=1933710#post1933710](http://ubuntuforums.org/showthread.php?p=1933710#post1933710)

[http://ubuntuforums.org/showthread.php?t=89584](http://ubuntuforums.org/showthread.php?t=89584)

---

### Post by mikkelrev on 2008-02-07
Woah guys, I just want to say THANK YOU. 

Just got 1440x900 on external monitor working on my Thinkpad X31 with Radeon 7500. After having tried for over a week.

Tonight I will sleep with a smile on my face.

Good night.

---

