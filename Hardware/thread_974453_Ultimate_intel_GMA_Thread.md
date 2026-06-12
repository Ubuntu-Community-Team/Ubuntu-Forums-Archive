---
title: "Ultimate intel GMA Thread"
date: 2008-11-07
forum: Hardware
---

### Post by Hibby on 2008-11-07
Right, I've spent ages searching these forums for a solution to my GMA 945 problems.

Y'see, it was all working fine, once upon a time.

Then i upgraded some stuff and all of a sudden Compiz broke. So after playing around with xorg.conf, I got that back.
Then, I decided I wanted a dual monitor set up. This seems to be a hard thing to do with a laptop GMA 945, and many people have this as a problem. So - here is the solution, written out and explained so that those reading can understand what they're doing to their system!

For those of you who are new to Ubuntu, Linux and // or the X server, when I mention xorg.conf, I mean /etc/X11/xorg.conf. This is a vital system file for making your Graphical Interface appear on your monitor, instead of pure text-based computing.

I started by copying xorg.conf into a folder named xorg in my home directory twice, a working backup and a new version:
```
$cp /etc/X11/xorg.conf xorg/xorg.conf.old
$cp /etc/X11/xorg.conf xorg/xorg.conf.new 
```

All the work I do from here on is in xorg.conf.new in my favourite text editor - nano for me, but some may prefer a graphical one. I don't know what these are in Gnome because I'm an xfce man!

I found that it was best to declare my GMA 945 in xorg.conf. This way, I knew that X knew it was there, despite the fact it's disappeared. For me, this looks like this:

```
 Section "Device"
    Identifier    "Intel 945"
    Boardname    "Intel 945"
    Busid        "PCI:0:2:0"
    Driver        "intel"
    Vendorname    "Intel"
    Option          "monitor-VGA" "foo"
        Option          "monitor-LVDS" "bar"
EndSection
```

Notice the two monitors I've declared as options - "monitor-VGA" is my external monitor connected to the VGA port, and "monitor-LVDS" is my laptop's monitor.
I've given them names of "foo" and "bar" for this tutorial.

Onto monitor "foo":
```
Section "Monitor"
    Identifier      "foo"
    Option "PreferredMode" "1440x900"
    Option "Position" "1280 0"
    Option "RightOf" "bar"
EndSection
```

As I declared earler, foo is my external monitor. "PreferredMode" is the resolution I want it to run at - 1440x900 is my LCD panel's native resolution. "Position" is where I want it to appear on my virtual screen (more on that later). It starts at 1280 0 , where 1280 is the x coordinate and 0 is the y coordinate. This means that It starts exactly where my laptop's (1280 px wide) monitor ends. "RightOf" "bar" is me reinforcing the fact that this is where it starts. I couldn't get it to work without this, but that might just be me being daft!

Onto Monitor "bar":
```
Section "Monitor"
        Identifier      "bar"
    Option "PreferredMode" "1280x800"
    Option "Position"  "0 0"
    Option "LeftOf" "foo"
EndSection
```

This is similar to foo, with my preferred mode, position of 0 0 on the virtual screen and to the left of foo.

Onto the Screen section:

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel 945"
    Monitor       "bar"

        DefaultDepth  24

        SubSection "Display"
                Virtual                 2720 900
        EndSubSection
EndSection

```
This is me defining that the two monitors will be connected in one large, virtual screen and outputted by the GMA945
I've left the default xorg definition of Default Screen for this one, as it makes life easier later on!
Here I reference the device "Intel 945" as what is providing the output for this big virtual screen.
I tell it which monitor to output on by default, which is bar. I don't need to reference foo, or so I am led to believe.

DefaultDepth is another corg default I left in.

This subsection is where the magic happens  - the x coordinate is the sum of my two horizontal resolutions (1280+1440)pixels and the y coordinate is my tallest monitor's resolution, 900pixels. Essentially it creates a big screen, which both my monitors display, and each one has a position in it, defined in their respective sections. If the screen is over 2048 pixels in either direction, then compiz won't work - this is a limitation of the intel drivers at the moment and I'm sure in time may well be sorted.

Finally, ensure that your ServerLayout has a reference to whatever you called your screen - if you left it the same as it was, then you don't have to worry about this, but if you changed your name be sure to change the Screen entry respectively.

Save xorg.conf.new and open up your terminal, and use this command:
```
 $ sudo cp xorg/xorg.conf.new /etc/X11/xorg.conf 
```
and restart your x server (ctrl+alt+backspace)
This copies in the new xorg.conf we just made to be the active one, and then restarting X means it gets used!
If all you get is a terminal, you've done something wrong, so login and use these commands to get yourself out of trouble:
```
 $ sudo cp xorg/xorg.conf.old /etc/X11/xorg.conf
           $ startx
```
This copies the old version of xorg.conf into /etc/X11/xorg.conf to become your active one, and we know that works already!
and then come back here and find your flaw!

Hope this is useful - I've gained a lot from this community and it's time for me to give back!


Hibby

(interpreted from [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) and humanised by me)

---

