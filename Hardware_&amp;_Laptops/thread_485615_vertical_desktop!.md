---
title: "vertical desktop!"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by Sushubh on 2007-06-27
i got this new dell lcd monitor which also turns vertically.

two questions:

would it require linux drivers to support the highest resolutions it can support?
how can i turn the display vertically so that i can try using the screen vertically!

---

### Post by olejorgen on 2007-06-27
This might depend on your video card..

I have a Nvidia card and I've put 
```

Section "Screen"
  Option "RandRRotation" "true"
  // etc...

```
in my xorg.conf

After this (and a X restart) you should be able to use **xrand** to rotate. I'm not sure how you change the resolution, but if you find a command that do this it should be simple to glue together a script.

This is my script to rotate my tablet pc screen: (partially taken from some howto)
```

#!/bin/sh
orientation=`/usr/bin/xrandr --query | /bin/grep "Current rotation" | /usr/bin/awk '{print $4}'`
if [ "$orientation" = "normal" ]; then
/usr/bin/xrandr --orientation inverted
/usr/bin/xsetwacom set stylus Rotate 3
else
/usr/bin/xrandr --orientation normal
/usr/bin/xsetwacom set stylus Rotate none
fi

```
Just ignore the wacom stuff

---

### Post by Sushubh on 2007-06-27
oi that's complicated. no gui interface!

i have a nvidia mx440 64 megs.

---

### Post by olejorgen on 2007-06-27
Sorry that I scared you :)

You could try
```

sudo apt-get install gnome-randr-applet

```
Then add "Display geometry switcher" to your prefered panel.

---

### Post by Sushubh on 2007-06-27
ok i did that. but that panel bar just gives me the resolutions not orientation. is it coz of my vintage graphic card?

---

### Post by olejorgen on 2007-06-27
Hm.. did you add
```

Option "RandRRotation" "true"

```
in your screen section in /etc/X11/xorg.conf and restarted (X)

(be sure to take a backup first)

Step-by-step:
```

cp /etc/X11/xorg.conf ~/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

```
Find
```

Section "Screen"

```
and add Option "RandRRotation" "true" like this:
```

Section "Screen"
  Option "RandRRotation" "true"
  // other stuff
EndSection

```
Save, close all running applications, and press CTRL-ALT-BACKSPACE (resarts your gui)

---

### Post by Sushubh on 2007-06-27
ah right i did not do that. but i did by choice selected 320x240 resolution... :P was pretty tough to get back to regular resolution!

ook. which section to add that code? device? display?

---

### Post by Sushubh on 2007-06-27
umm screen.. ok doing that now! ctrl shift f12 to restart x?

---

### Post by olejorgen on 2007-06-27
ups, things happen quick :P I editet my previous post to be more clear

---

### Post by olejorgen on 2007-06-27
> **Sushubh said:**
> umm screen.. ok doing that now! ctrl shift f12 to restart x?
Hm.. haven't heard of that one, but sure, if it restart X go ahead. (save all documents first)

---

### Post by Sushubh on 2007-06-27
no changes... here is the screen section in my conf file:

> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "700S"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "AddARGBGLXVisuals" "True"
							Option "RandRRotation" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Sushubh on 2007-06-27
btw. i moved from a 17" crt to 19" lcd... the resolution list remains the same... how to tell the comp to regenerate the list to add the resolutions supported by the new monitor? :P

---

### Post by olejorgen on 2007-06-27
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
add RandRRotation again and restart X. (but be sure to back up your xorg.conf for your original monitor)

Then try 
```

xrandr --orientation inverted
echo "a little later..."
xrandr --orientation normal

```

---

