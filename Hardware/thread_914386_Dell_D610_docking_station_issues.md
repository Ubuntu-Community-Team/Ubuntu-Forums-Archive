---
title: "Dell D610 docking station issues"
date: 2008-09-08
forum: Hardware
---

### Post by Coreo on 2008-09-08
Hey ubuntuforums.

I have a Dell Latitude D610 with Hardy Heron. Installed it about a month ago, and so far it works great!

I've just lately been having problems when I tried to use my docking station. I have a port replicator, right from Dell, that has audio out, video out, usb ports, etc.
The USB ports all work for mouse, keyboard, and external HD input, but I'm having problems with the video output.

My external monitor's native resolution is 1600x1200, but when I dock my computer, the maximum resolution available to me is 1024x768, which is the max resolution of my internal laptop display.
1024 looks alright, but really does not do my monitor, or Ubuntu justice.

Is there are way to set a higher external resolution?
Also, the CRT/LCD function key does not appear to do anything, other than black both the internal and external display for a second. I don't know if this is normal or not while using the docking station.

If anyone has had a similar problem, or is able to help, I would greatly appreciate it!
Thanks!

PS. I'm no n00b to linux...gimme all the techy-talk if you know it. Haha.

---

### Post by Coreo on 2008-09-09
Bump.

---

### Post by dro0g on 2008-09-11
do a search for xrandr - I still haven't found a perfect way of dealing with this, but xrandr is what I use in a script to change res when docking/undocking and when using a 2nd monitor. 

This is what I use with my D630 with a 2nd monitor to turn it on and off:
```
xrandr --output VGA --right-of LVDS --auto

# to shut off
# xrandr --output VGA --off

```

---

### Post by Coreo on 2008-09-11
I think I've tried that before...

I tried it again, and neither of the commands do anything.

It could be because I didn't dock it while my laptop was on. I had it docked, and I powered it up.
It sounds strange, but this actually makes a difference.

---

### Post by Coreo on 2008-09-11
Also, if I close my laptop after I've docked it, it turns off the internal screen, and also the external screen.
It seems like it doesn't know there are 2 separate displays, but thinks there is just one...

---

### Post by Coreo on 2008-09-18
Bump bump?

---

### Post by bhp666 on 2008-10-04
this worked for me

```
sudo gksu displayconfig-gtk
```



just selected my monitor and so on - or a generic one with screen resolution of your liking

if your monitor is listed... bonus!

---

### Post by Coreo on 2008-10-08
That doesn't work for me.
Every time I attempted to set a new monitor, or a new resolution, it would fail and give me the error "Unable to set new mode". It would then go to "low graphics mode" and ask that I set it back to a working configuration, basically.

The resolution or display configuration would never be applied, or even saved until the next time I opened the display config.

Sometimes even if I opened the window and didn't change anything, it would still go to low graphics mode.

It's pretty confusing..nothing seems to be working.
It looks like I'll have to get into manually editing the xorg.conf file, but I'm not entirely sure of how to do it. I've seen lots of people making changes, but none of them seem to apply perfectly, so I don't want to use their examples.

---

### Post by Coreo on 2008-10-08
Update:
Displayconfig doesn't even run now.
It asks for my admin password, but then never actually launches.


Any way to do it more manually?

---

### Post by benbelly on 2008-11-01
Are you still having trouble?  I have a Latitude D630 that I use with the docking station.  I never use both the laptop screen and the docking screen at the same time, so I don't have any experience with that.  When I power on the laptop while it's in the docking station, the external monitor is detected correctly and used.  I vaguely recall (it's been about 6mos) that I had to set a virtual screen size. Does that ring a bell? I poke around and see what happens.

  When I put the laptop into the docking station while powered on, I have to do something goofy.  I open a terminal and type: ```
sleep 10; xrandr --auto
```  This command waits ten seconds, then re-detects the displays.  That gives me a few seconds to close the laptop and put it in the dock.

  Anyway, if you're still having trouble, let me know.  Maybe I can help.

-Ben

---

### Post by Coreo on 2008-11-05
Hey.

I haven't been able to get anything working yet, but it's been a few weeks since I've really tried again.

If I drop my laptop into the dock, and then boot, it detects the external screen, and shows the bootup and everything on it, but it still doesn't go to the correct resolution, or change to what I try to set it to.
If I have my laptop on and then drop it in, the mouse and keyboard and everything else functions properly, but the display is usually not recognized and does not turn on.
I do a Ctrl-Alt-Backspace, log in again, and then it detects it.
But it still has the problem that I can't change the resolution of the external screen.

And I've heard of Virtual Screen size, but haven't checked in to it. I don't remember seeing anything about that in some of the other attempted fixes to this problem. Maybe I'll have a look into it....

Thanks!

---

### Post by frogotronic on 2009-01-07
What video card are you running?  Intel, ATI, or nVIDIA?

---

### Post by Coreo on 2009-01-08
I am running the ATI X300 card.
....as far as I know.

---

### Post by frogotronic on 2009-01-08
> **Coreo said:**
> I am running the ATI X300 card.
....as far as I know.

Are you running the restricted drivers? FGLRX?  Check under System>Adminstration>Hardware Drivers

- CH

---

### Post by Coreo on 2009-01-08
I'm using the proprietary drivers.

I think I tried using fglrx a while ago....it's been so long since I tried fixing all this.

---

### Post by frogotronic on 2009-01-09
Okay, so to get different resolutions on two different monitors, you'll need to run FGLRX (or maybe the radeon driver).

My experience is with the FGLRX driver, so that what these instructions will be for - The FGLRX driver from the repos will work, but is has a number of bugs with movies, compiz, etc.  You'll want to install the 8.12 driver.  (You could skip to step 2 and try the configuration without installing the 8.12 drivers...)

**1) Install the FGLRX driver according to METHOD 2 of these instructions:**

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Remember to remove/uninstall the ATI accelerated driver by unchecking the box in System>Administration>Hardware Drivers *before* trying METHOD 2.

The FGLRX driver in the Hardy repos is old and has a number of bugs - the current (8.12 Catalyst Driver) doesn't.

**2) After install and reboot, execute the following command**

```
sudo aticonfig --initial -f
```

**3) Then edit the bottom (last couple of sections of your xorg.conf file to look like this:**

```
$sudo gedit /etc/X11/xorg.conf
```


```
Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Option      "VideoOverlay" "off"
	Option      "OpenGLOverlay" "on"
	Option      "TexturedVideo" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		*Modes    "1280x1024" "1280x800" "1024x768" "800x600"*
	EndSubSection
EndSection

```

Where the first two modes are resolutions on your external monitor (1600x1200) and your laptop (AAAAxBBBB) monitor.

[B]4) Reboot
[/B]
**5)** You should now be able to choose the arrangement/resolutions of screens using the **_ATI Catalyst Control Centre_** (see attached screenshot).  Probably under Applications>Accessories (or somewhere else in your GUI menu)

   Your Hardware Drivers should also have a green light, but no checkmark (see screenshot).

   I've also included my complete xorg.conf file (for reference).


Let us know is this works.

- CH

---

### Post by Coreo on 2009-01-12
Hey, thanks a lot CH!

I just kind of dismissed the idea of getting it working for a while, so it's great to finally have a solution.... Lol.

I'll try it out this evening or tomorrow when I have more time, and I'll let you know how it works.

Add:  Is there any way to disable the laptop screen when it is docked? I noticed a post by Ben in this thread from a little while back about docking and setting up the screens. When I have the laptop docked, the laptop screen never turns off completely. This isn't a big concern, it would just be nice.

Also, a little while back I figured out how to successfully boot up and use my external monitor at 1600x1200. It's a trick of dropping it into the dock at the right time...but I don't remember exactly how I did it.


I'll try out that fix in a little bit.

---

### Post by frogotronic on 2009-01-12
> **Coreo said:**
> Hey, thanks a lot CH!

I just kind of dismissed the idea of getting it working for a while, so it's great to finally have a solution.... Lol.

I'll try it out this evening or tomorrow when I have more time, and I'll let you know how it works.

Add:  Is there any way to disable the laptop screen when it is docked? I noticed a post by Ben in this thread from a little while back about docking and setting up the screens. When I have the laptop docked, the laptop screen never turns off completely. This isn't a big concern, it would just be nice.

Yes, I can't remember the commands (it was in a post on these forums) but basically you need to force the drive to output the external even when your lid is closed.  Don't forget to adjust your power settings in Gnome Power Manager.

- CH

---

