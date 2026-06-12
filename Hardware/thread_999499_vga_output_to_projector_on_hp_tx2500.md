---
title: "vga output to projector on hp tx2500"
date: 2008-12-01
forum: Hardware
---

### Post by a_toff on 2008-12-01
Hi folks,

I have a hp tx2500, and I'm having trouble with a few things, namely getting VGA output to work with a projector. I have the restricted ATI fglrx driver installed. When I plug-in the projector, the program called Screen Resolution (menu/System/Preferences) seems to recognize it, but the projector doesn't seem to be receiving any signal.

Does anyone have any tips to suggest or perhaps some links to related topics? (I've tried searching around about this for the past few days but have had no luck.)

Thanks kindly

---

### Post by elijah-man on 2009-01-28
I am having a simler problem:
Trying to get my external monitor working as an extended desktop at native resolution, and not having much luck.  I have spent a couple days looking all over the internet and have found no good solution.  Here's what I have:

HP tx2500 (2510us), 2.1GHz, 3GB, 250GB
AMD Turion X2 Ultra 64
ATI Radeon HD 3200
Ubuntu 8.11
Kernel 2.6.27-7
Xorg 7.4
GNOME 2.24

Displays:
LVSD - 1280x800 12"
VGA - 1920x1200 26" (25.5") Westinghouse LCD

It sends signal to the external display (at 1024x768) during startup and during the loading bar, but as soon as the login screen comes up on the laptop, the external monitor loses signal, and never regains signal until the shutdown loading bar screen.  I can configure both of the screen resolutions just fine and arange them how I want them in System>Preferences>Screen Resolution.  I tried running xrandr to see if there was a problem with my resolution, but it confirmed that my resolution was ok with this output:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1920 x 1600
VGA-0 connected (normal left inverted right x axis y axis)
   1920x1200      60.0 +   60.0 
   1600x1200      60.0     60.0 
   1680x1050      69.9     60.0     60.0 
   1600x1024      60.2 
   1400x1050      70.0     60.0 
   1280x1024      75.0     60.0 
   1440x900       59.9     60.0 
   1280x960       60.0 
   1360x768       59.8 
   1280x800       60.0 
   1152x864       75.0     75.0     70.0     60.0 
   1024x768       75.1     75.0     70.1     60.0 
   832x624        74.6 
   800x600        72.2     75.0     60.3     56.2 
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9 
None connected (normal left inverted right x axis y axis)
   1360x768       59.8 
   1152x864       60.0 
   1024x768       60.0 
   800x600        60.3 
   640x480        59.9 
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+
   1024x768       60.0 
   800x600        60.3 
   640x480        59.9

I still get no signal to the external monitor, I assume when Xorg is running.  I also tried installing the ATI Driver FGLRX and no sucess.  The ATI Driver works for "faking" a wider desktop (IE making one desktop that's twice as wide), but I cannot achieve native resolution on the external display, which is important to me for photo editing.  Playing around with installing and uninstalling drivers, the simulated desktop grew to over 7000 pixels wide, so I finally gave up on it and did a fresh 8.10 install.  I am a beginner, but I can use terminal just fine as long as you tell me what to enter. Any help would be greatly appreciated.

Thanks,Eli

---

### Post by a_toff on 2009-01-29
Yes, this looks like it could be the same problem.

I've found, however, that vga ouput works while the machine is booting-up and from the login-prompt. I tried creating a new user, and when I log into this new account, voila!, I have VGA output. So something must be conflicting with regard to settings I've changed since installing... for example getting the wacom tablet functions working properly.

---

### Post by kg6gfq on 2009-01-29
I'm currently using a second monitor for an extended desktop, and could potentially use it as a clone of the LCD panel (I assume you'd want it cloned for projection).  

Haven't tried the "log in as a new user" trick, and I'm not quite sure how that would work, but I'll give it a go later.  

Right now, I'm using the RadeonHD driver from RadeonHD's git repository.  I've posted about it before, the pertinent links are:
[http://www.x.org/wiki/radeonhd#head-107f8ec30e84804907b4af6cdb20fbdd0056eefb](http://www.x.org/wiki/radeonhd#head-107f8ec30e84804907b4af6cdb20fbdd0056eefb) (how to download and install)
[http://ubuntuforums.org/showpost.php?p=5913207&postcount=249](http://ubuntuforums.org/showpost.php?p=5913207&postcount=249) (setting up xorg.conf)
[http://ubuntuforums.org/showpost.php?p=5961083&postcount=260](http://ubuntuforums.org/showpost.php?p=5961083&postcount=260) (fixing the install, because it goes to the wrong place in ubuntu)
The advantage of RadeonHD is that it allows you to change the display settings without restarting X by using xrandr (or something like grandr if you want a gui).  However, it doesn't support screen rotation or 3d acceleration.  

If you need 3d acceleration you should use xinerama with the fglrx driver...  I lost the xorg.conf I had set up for that, but I could probably recreate it if you can't find enough info via google.  

Unless I'm mistaken, it's impossible to rotate the screen while using a second monitor - I think xinerama and randr are incompatible - but you can try using xinerama with the radeon driver rather than fglrx if you want.  

Hope that's helpful!

---

### Post by elijah-man on 2009-01-30
So I tried installing radeonHD (1.2.4) according to the instructions on the websites you linked, but either I did not do it right, or it did not help.  I think I got it installed in the right place but I am not sure.

I made another user name and tried that, but that did not help either.

In fact, I have tried everything I could think of or find on the Internet.  I have tried every Wiki, every how-to, every suggestion on every message board I found, tried screwing around with xrandr, xorg.conf, tried a number of command line programs people recommended, and nothing helped.  I had to repair my xorg.conf file about a dozen times, and messed up everything so bad a couple times that I am on my 3rd clean install (8.10) in three days.  

During startup and shutdown, the external monitor displays at 1024x768 (native resolution is 1920x1200), but as soon as I get the splash screen, the external monitor flashes "no input signal" and goes blank.

If I install fglrx, it will allow me to mirror or use extended desktop (one large virtual display), but will not allow me to do either at native resolution, which is really the whole point for getting such a large display.

After my 2nd clean install, I left the room to go make lunch/breakfast/snack/whatever (time has lost all meaning the past couple days), and when I came back the external monitor had started mirroring my LVDS.  It was only displaying at 1024x768 though (LVDS was displaying the same), so that's not even the right dimensional ratio (should be 16:10, not 4:3).  I used xrandr to configure the LVDS from 1024x768 to 1280x800.  So far, so good.  Thinking I might almost have it, I went ahead and configured the external monitor for the correct resolution and position, and the external display promptly said "no signal input" and went blank.  WTF!
Using xrandr, it confirmed that I had in fact changed the resolution and position, and that it was active... seriously, WTF!

After trying a whole bunch of other stuff and getting my virtual display to almost 7000x1200 (again), I decided to do yet another fresh install.

Using System>Preferences>Screen Resolution, I am able to set LVDS to display at its native resolution (1280x800), as well as setting up VGA as an extended desktop at native resolution (1920x1200) to the right of the LVDS.  This gives me a virtual display of 3200x1200.  All this seems to work, but there is still no signal TO the VGA.  The monitor is on (and continues to be on through several restarts), and xserver detects the monitor (giving me the appropriate resolution choices and labeling it with an appropriate name) so there is clearly signal coming FROM the external monitor, and the VGA port is clearly functional.  I can even pick up windows and drag them onto the extended desktop (and I can watch where it is by watching the workspace indicator in panel), so I know the computer is treating it as if the display is actually there, it is just not transmitting a signal to the VGA port.

I have hooked my roommates computer (running 8.4) up to my monitor, and it mirrored ok, but not at native resolution.  I did not try setting his up for extended desktop so I don't have too much info on that, but at least it gave me hope :cry:

I have attached outputs from xrandr, lspci, xorg log, dmesg, and my xorg.conf in a tar file if anyone thinks they might be able to help.  If you need any more information, just let me know what to paste into terminal and I will post the output.  I have tried everything I could think of, so now I turn to the greater community in a desperate plea for help.  Honestly I don't care too much about 3D, mirroring, or extended desktop (I don't care if I have to turn off LVDS to switch to VGA) as long as I can get a signal to VGA at 1920x1200.  If anyone can help me figure this out I would be forever in your debt.  

Thanks, Eli

---

### Post by elijah-man on 2009-01-30
Update:

So I left my computer running over night.  This morning I woke up my computer by swiveling the mouse around, and suddenly the external monitor was mirroring the LVDS, but not at native resolution.  I looked in System>Preferences>Screen Resolution, and it still says I am using extended desktop with the correct (1920x1200) resolution for the external monitor.  I can still drag windows onto the extended desktop as well, although I only know where they are by looking at the "workspace" indicator in panel.  I looked through the settings menu on the monitor its self, and found that it is only receiving a 1024x768 signal.  Both sides of the mirrored display are cut off with the external monitor.  Where did they go?  I can use the settings menu in my external monitor to display at optimal aspect ratio (which keeps the image from being stretched), but the edges are still cut off, and it still looks like crap (text is all wavy).  

I tried messing with System>Preferences>Screen Resolution and the external monitor promptly lost signal (yet again).  In xrandr, what is the middle display "none connected" all about?  
> eli@the:~$ xrandr
Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 3200 x 1200
VGA-0 connected 1920x1200+1280+0 (normal left inverted right x axis y axis) 550mm x 309mm
   1920x1200      60.0*+   60.0  
   1600x1200      60.0     60.0  
   1680x1050      69.9     60.0     60.0  
   1600x1024      60.2  
   1400x1050      70.0     60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9     60.0  
   1280x960       60.0  
   1360x768       59.8  
   1280x800       60.0  
   1152x864       75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
None connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS connected 1280x800+0+400 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

I have an S-video port that I am not using, could that be it?  Is there a way to make it go away?  Might that fix my problem?  I really don't know; I'm just throwing out ideas.  HELP!

---

