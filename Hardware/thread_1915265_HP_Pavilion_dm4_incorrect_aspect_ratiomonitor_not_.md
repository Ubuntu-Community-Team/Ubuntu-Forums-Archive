---
title: "HP Pavilion dm4 incorrect aspect ratio/monitor not detected"
date: 2012-01-25
forum: Hardware
---

### Post by jcg5230 on 2012-01-25
Hi guys,

I recently installed Ubuntu 10.04 on a new HP Pavilion dm4, and a lot of things did not work right after installing.  One of the most frustrating is the aspect ratio - everything on the screen is stretched horizontally.  I've spent a few days trying to fix it already.  Here's what I know:

In System->Preferences->Monitors, no monitors are detected.  The only options for the aspect ratio are 1024x768 and 800x600, but my screen needs a 1366x768. Clicking the "Detect Monitors" button does nothing.

Anyway, I tried to find out how to get a monitor detected (I've been assuming that's the right approach and that laptop screens are viewed by Ubuntu as monitors. Maybe that's where I'm wrong).  I don't have an xorg.conf file, but I have an xorg.conf.d/ directory with the following files in it:
05-evdev.conf  10-synaptics.conf  10-vmmouse.conf  10-wacom.conf

None of these seemed to be what I needed, so I followed some instructions to add my own monitor file, 10-monitor.conf, with the following code in it:

Section "Screen"
    Identifier    "Screen0"
    Device        "Device0"
    Monitor       "Monitor0"
    DefaultDepth  16 #can be 16 or 24                                                                                             
    SubSection "Display"
        Depth     16
        Modes     "1366x768_75.00" #resolution                                                                                 
    EndSubSection
EndSection

I saved it in the same directory and restarted, but nothing changed.  I'm stumped.  I'm relatively new to linux, so maybe I'm just missing simple.  Any suggestions? This stretched screen is driving me crazy...

jcg5230

---

### Post by Corporate Boy on 2012-02-05
If it matters I'm suffering with the same issue.  This is a new lap top and fresh install.  I started with with Ubuntu 11.10, but Eclipse did not play nicely with it, but at least the aspect ratio was correct.  I reverted back to 10.04 and I have the same aspect ration issue.  I just started investigating, but I'll let you know what I find.

---

### Post by rtalcott on 2012-02-19
Same problem...new hp dm4 with 12.04 on it...was able to beat the black screen but not the incorrect aspect ratio on the display.
rt

---

### Post by Favux on 2012-02-19
AFAIK you still need to put video sections in the xorg.conf, not xorg.conf.d.  For instance the proprietary Nvidia and ATI drivers may still create a xorg.conf.  You can create a xorg.conf by entering in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
and hitting Save.

Depending on whether you need a modules section it would look something like this:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```

But don't mess with X configuration files unless you know how to remove them or edit them or restore them from back up with the command line from the Recovery Boot.  Changing them can break X leaving with just the CLI.  And once you get a working xorg.conf back it up.

---

### Post by rtalcott on 2012-02-20
At this point I can use the machine although it's not optimal...I don't want to create a larger mess so I'll wait for a well defined solution to come along.
rt

---

### Post by jcg5230 on 2012-03-28
bump

---

### Post by Mark Phelps on 2012-03-29
> **jcg5230 said:**
> bump

That's certainly not terribly informative!!

Did you do the stuff that favux indicated? Did it work?

If it didn't, what happened?

Just bumping to bump does no good.

---

