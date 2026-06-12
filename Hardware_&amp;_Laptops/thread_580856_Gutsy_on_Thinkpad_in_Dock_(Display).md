---
title: "Gutsy on Thinkpad in Dock (Display)"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by chloraldo on 2007-10-19
I have a Thinkpad T43p laptop. I used Feisty Fawn which worked well. I decided to install Gutsy (clean install formatting disk). Everything works well, except that I cannot use the laptop in the dock with an external monitor.

The external monitor has 1280x1024, the internal monitor has 1400x1050.

Has anyone managed to get this working?

Thanks for your help?
chlori

---

### Post by cversion7 on 2007-10-19
I, too, am having a similar issue. Thinkpad T60 in dock. When I try to enable the second monitor, its model is "undetected" and is stuck at 640x480. If I manually change it to generic LCD 1280x1024 and hit OK, then it says all users must log out for changes to take effect. I reboot and then the GUI won't startup for the login screen giving me a message that I'm in some low resolution mode putting my main monitor to 800x600 with no output to the second still. I cannot seem to do anything at that point other than replace my xorg.conf with a backup, reboot again and I'm back where I started. 

My video driver defaults as VESA as I cannot get the ATI driver to work at all after many hours of trying (mobility x1400).

---

### Post by chloraldo on 2007-10-19
> **cversion7 said:**
> I, too, am having a similar issue. Thinkpad T60 in dock. When I try to enable the second monitor, its model is "undetected" and is stuck at 640x480. If I manually change it to generic LCD 1280x1024 and hit OK, then it says all users must log out for changes to take effect. I reboot and then the GUI won't startup for the login screen giving me a message that I'm in some low resolution mode putting my main monitor to 800x600 with no output to the second still. I cannot seem to do anything at that point other than replace my xorg.conf with a backup, reboot again and I'm back where I started. 

My video driver defaults as VESA as I cannot get the ATI driver to work at all after many hours of trying (mobility x1400).
That's exactly what happens in my case. Thanks for the detailed description. I really hope someone can help us here...

---

### Post by Lil on 2007-10-19
Look at this thread here; which should help you solve this:

[http://ubuntuforums.org/showthread.php?t=580967](http://ubuntuforums.org/showthread.php?t=580967)

I have posted a few solutions. If you use the open source 'radeon' driver in xorg.conf you can configure this in xrandr on the command line. The new ATI/Radeon drivers in Gutsy don't support Xinerama for dual displays any more.

That thread and the link to a post on my blog should really help you.

For starters boot your ThinkPad with the monitor plugged in, open a Terminal and type:

xrandr

This should tell you on LVDS you have modes up to 1024x768 (or 1400x1050) and VGA-0/DVI-0 has a monitor of whichever capabilities it too detects...

Hope this helps :)

Vicky

---

### Post by cversion7 on 2007-10-19
Okay after working on this for another hour (looking through that other post for info, including copy/pasting vis_e's xorg.conf information into mine) and I still am stumped. I cannot even get my system to accept any ati or radeon driver aside from the VESA one. If I change it (whether via xorg or the Screens and Graphics option) it will either change itself back to VESA or require "all users to log out" where the screen loads in "low graphics mode" at 800x600, every single time. 

"If you use the open source 'radeon' driver in xorg.conf you can configure this in xrandr on the command line."  

I can't get it to accept radeon as an option so I can't even get to the point to try xrandr. I don't know if I'm supposed to try messing with it in this "low graphics mode" or not as nowhere does your information mention this...

I'm using a clean install of 7.10RC1 updated to 7.10 Final. I've gone through a half-dozen other "how tos" on setting up the ATI drivers trying to get desktop effects working, none of which worked. At this point I had given up the hopes of playing games while I'm traveling and just sticking with 2d... but at work I need the dual monitor support since without it, the larger monitor on my desk is blank and makes it look like I'm just screwing around (which, of course, I am but I don't want anyone to know that). 

Maybe I've screwed something up where the open source driver just won't work right as I was sifting through 150 pages of "ZOMG COMPIZ ATI" posts trying to get a driver to work correctly. Worst case, I'll just reload with the 7.10 Final disk I'm downloading and start over... /sigh (and I thought getting Lotus Notes 8 for Linux to work was tough... it was a breeze by comparison)

---

### Post by chloraldo on 2007-10-19
> **Lil said:**
> Look at this thread here; which should help you solve this:

[http://ubuntuforums.org/showthread.php?t=580967](http://ubuntuforums.org/showthread.php?t=580967)

I have posted a few solutions.

Thanks, it nearly worked how I wanted it to...
I could adjust the resolution for my external monitor. The problem I still have is that it cuts off the right edge of the desktop. I'm not extending the desktop - both monitors should show the same thing...

Any ideas what that could be? xrandr recognised the correct resolution...

---

### Post by Lil on 2007-10-19
> **chloraldo said:**
> Thanks, it nearly worked how I wanted it to...
I could adjust the resolution for my external monitor. The problem I still have is that it cuts off the right edge of the desktop. I'm not extending the desktop - both monitors should show the same thing...

Any ideas what that could be? xrandr recognised the correct resolution...

Ok this is 'normal', you need to now tell xrandr to extend onto this monitor. Assuming it's on the right of the laptop:

xrandr --output VGA-0 --right-of LVDS

Hey presto. :)

Vicky

---

### Post by chloraldo on 2007-10-19
> **Lil said:**
> Ok this is 'normal', you need to now tell xrandr to extend onto this monitor. Assuming it's on the right of the laptop:

xrandr --output VGA-0 --right-of LVDS

What if I want to just use the external monitor?

It just cuts of about 1cm...

---

### Post by Lil on 2007-10-19
> **chloraldo said:**
> What if I want to just use the external monitor?

It just cuts of about 1cm...

I would fill you in on fixing the cut off bit but I'm on Feisty right now at home.

To turn off the laptop panel:

xrandr --output LVDS --off

To turn on the laptop panel

xrandr --output LVDS --auto

To turn off VGA-0

xrandr --output VGA-0 --off

Vicky

---

### Post by chloraldo on 2007-10-19
> **Lil said:**
> I would fill you in on fixing the cut off bit but I'm on Feisty right now at home.

To turn off the laptop panel:

xrandr --output LVDS --off

To turn on the laptop panel

xrandr --output LVDS --auto

To turn off VGA-0

xrandr --output VGA-0 --off

That solved the problem:
xrandr --output LVDS --off

That turned off the laptop AND sorrected the width of my external monitor!

Now is there a way to have both? An easy way to switch monitors:
- both monitors, extended desktop
- just external
- just laptop

Thanks for your help!

---

### Post by cayhorstmann on 2007-10-20
Lil--you are my hero! I have struggled for a long time with the wretched Screens and Displays utility, and I was never able to get dual display to work. But xrandr --output LVDS --auto works like a charm. (I had stared at the xrandr usage for some time and never figured out that's how you were supposed to invoke it :-()

---

### Post by Lil on 2007-10-21
Well today might be your lucky day.

I've written a script that can be:

 - run from the command line
 - or attached to Fn + F7

That will switch between:

 - Laptop Display Only
 - VGA Display Only
 - Laptop + VGA Mirrored
 - Laptop Display extended onto VGA Display

It's very simple and doesn't allow you to tweak the resolution but it detects the best resolution for each panel and uses that, thanks to xrandr.

I'm just testing it now but it works a charm so far :) Eventually I hope to create something in PyGTK so there's a GUI as well. I suppose this isn't the usual way one sets up their screens but it works well and doesn't require any knowledge from the user.

Also it won't switch the display if no VGA display is physically connected but if you have it say on VGA Output Only, then unplug it, leaving no video output, one strike of Fn + F7 sorts it back out again (assuming you attached the script to the Fn + F7 keycode.)

I don't know any PyGTK (not really) so a completely integrated solution might be a little while off, but if you can plonk a script in your home folder somewhere, and then use gconf-edit (bit like regedit) to add the script to the Fn + F7 keystroke, you'll be fine :)

Vicky

---

### Post by Lil on 2007-10-21
Ok I've done it:

[http://ubuntuforums.org/showthread.php?t=580967&page=2](http://ubuntuforums.org/showthread.php?t=580967&page=2)

See my posts on that thread for the switcher script and more information.

Vicky

---

