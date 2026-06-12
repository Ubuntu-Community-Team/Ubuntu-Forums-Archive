---
title: "ati+compiz=flickering video/open gl"
date: 2008-04-23
forum: Hardware
---

### Post by medivh on 2008-04-23
I don't want to believe that it is not possible to use compiz and other OpenGL applications at the same time. With such big community and open software is it that much hard to solve that issue? I read that it works with nVidia cards but not with ATI.

I am really about to switch Ubuntu from Windows XP but i hate this kind of problems i face everyday. Do i have to turn of compiz whenever i want to run google earth or any other 3D application :mad: or stand that flickering issues. I am using awn and when i turn off compiz it also goes and therefore i cant reach open windows list.It is meaningless to decorate and customize all desktop with these apps and then turn them off before running an application.

So i think instead of spending time for other things, developers must solve hardware and driver related issues first.

---

### Post by VeN0mizer on 2008-04-23
You can blame ATI for the really @$&*(@#$& driver quality. They only fix about one to two minor bugs a month with their drivers. Sometimes I swear they have their company janitors working on them. My desktop has an nvidia card and it runs FLAWLESSLY. I can run WoW with compiz with no hitches whatsoever. However, with my laptop, I too get flickering and odd effects. If I could rip this POS video controller off of my laptops motherboard and replace it, I'd do it in a heartbeat....keep looking for driver updates from ATI man, it's all the advice I can give you atm :/

---

### Post by Mr_Congeniality on 2008-04-23
I've had NOTHING but problems with ATI drivers.  My desktop used to have ATI, but I bought an NVIDIA 7900 GTX for it instead, and I couldn't be more happier.

Another situation, I had a dell E1505 and some dumb guy who was supposed to come and fix a fan problem with my laptop actually messed up the computer instead of fixing it, and I had a ATI card in that laptop, X1400 with hypermemory.  Dell had to ship me a new laptop, and it has an NVIDIA 8600M card.  There is definatly a difference between NVIDIA and ATI on Ubuntu.  Even though ATI might be ahead in the arms race for next-gen graphic support, you should stick by NVIDIA because they are clearly not forgetting that people use Linux, too.

---

### Post by moonbeam on 2008-04-23
I'd just like to point out that the Xorg (non-proprietary) ATI drivers are rock solid for a lot of the older ATI cards (r2xx,r3xx and I believe things are getting better for r4xx and r5xx).   I'm running an older (r350 based) ATI card with recent Xorg radeon drivers on my dev system, and they are extremely nice.

---

### Post by slippynuxx on 2008-06-18
What I find interesting about this bug (I experience it too) is that when my gnome-screensaver runs, there's a lot of flickering.  But, if I open up the System > Preferences > Screensaver window and do previews, no flickering.  That leads me to believe it's fixable.

---

### Post by markbuntu on 2008-06-19
If you want to fix the flickering widowed video problem you can edit the appropriate sections of your xorg.conf to look like this:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "off"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "DRI"
        Group       "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

Then run, in a terminal:

sudo aticonfig  --input=/etc/X11/xorg.conf

to write the changes to the actual ATI config file.

This will only work with the ATI driver 8.4 and newer. Also, you must have redirectfullscreenwindows checked in the compiz settings manager. 

The TexturedVideo "off" option can cause some full screen playback problems for older cards and slower cpus but will get rid of the windowed playback flickering. You can turn it back on for full screen high def playback if you need to.

ATI has recently made a great change in their commitment to linux, releasing source code to the driver writers groups, etc. They also seem to be committed to proprietary driver updates for newer cards about every six weeks which includes 3 weeks of testing before release.

They are aware of this problem with compiz and OpenGL and are working towards a solution. The 8.5 and 8.6 drivers have a lot of improvements over the 8.4 in the repos. The screensaver problem is fixed. The Compiz problem will be fixed soon. 

I expect that by the fall, ATI will be at least comparable to Nvidia.

---

### Post by ok123jump on 2008-09-27
Hmmm...

These suggestions didn't work for me. I have a Radeon 4870 HD.I still get flickering when I run "glxgears" or any screensaver.

Do you think this is a graphics card specific issue?

---

### Post by theApokalypsis on 2008-11-08
using the latest 8.10 drivers from ATI as they are doing a good job so far. I picked up a 4870 as well and even applying those reccomended settings I still get video flickering :S. A pain for animated desktops... All in all I am way more happy with ATI. With the nvidia drivers the 2D acceleration in for example css3/javascript web applications are slowed down to a crawl... 

Perfect with ATI. Does anyone know if ATI releases beta drivers before the 3 weeks of testing? 8.10 was released mid Oct so I would assume somethings bound to come out soon. :D

---

### Post by pelle.k on 2008-11-08
```
You can blame ATI for the really @$&*(@#$& driver quality.
```
No this is a problem with Xorg. Or, to be more precise the lack of DRI2. Intel has the same problem. The thing is nvidia bypassed some features in xorg and wrote their own propreitary hardware acceleration in their linux drivers.
DRI2 was supposed to be included in xserver 1.5 (wich is in intrepid), but there was a change of plans unfortunately, so DRI2 will be included in xserver 1.6 (to be released pretty soon).

DISCLAIMER - i use an nvidia card, and it works very well. But this doesn't change the fact that ATI's drivers would probably perform identically if it hadn't been for that recent DRI2 mishap.

---

### Post by kloispetie on 2008-11-10
After performing the above mentioned procedure; I get this message:

[I]Data incomplete in file /etc/X11/xorg.conf

	Undefined Screen "aticonfig-Screen[0]" referenced by ServerLayout "Default Layout".

aticonfig: Parsing the configuration file failed.

The above error messages are reported from XFree86 and may assist you in

diagnosing the problem with your configuration input file. Try use -f option

to generate a new configuration file.
[/I]


Anyone has an idea?


this is how my xorg.conf looks like after editing:

[I]Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier "aticonfig-Device[0]"
	Driver "fglrx"
	Option "XAANoOffscreenPixmaps" "on"
	Option "TexturedVideo" "off"
	Option "VideoOverlay" "off"
	Option "OpenGLOverlay" "off"
	Option "Textured2D" "on"
	Option "UseFastTLS" "1"
	Option "BackingStore" "on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 "aticonfig-Screen[0]" 0 0
	Option "AIGLX" "on
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option "RENDER" "Enable"
	Option "DAMAGE" "Enable"
	Option "Composite" "Enable"
EndSection

Section "Module"
Load "glx"
EndSection

Section "DRI"
Group "Video"
Mode 0666
EndSection
[/I]

Thank you very much

---

### Post by politas on 2008-11-11
After upgrading to Ubuntu 8.10, I've had serious video issues.

Made the xorg.conf changes suggested above. I have flicker-free video playback, but it seems to be using x11 by default now (mplayer only works by selecting x11), and I still can't run 3D games.

politas@wedge:~$ etracer
Extreme TuxRacer SVN Development --  [http://www.extremetuxracer.com](http://www.extremetuxracer.com) 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) for details.

*** etracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)
politas@wedge:~$

---

### Post by theApokalypsis on 2008-11-11
thanks for the info pelle :)

looks like its just going to be a matter of time. X11 playback for now I suppose (where a quad core comes in handy :D)

kloispetie, sorry, not too good yet at this stuff. :S. i could only suggest doing a fresh xorg.conf config, then aticonfig followed by the input command for saving any custom editing.

sudo dpkg-reconfigure -phigh xserver-xorg
sudo ati-config --initial
sudo ati-config --input=/etc/X11/xorg.conf


good luck.

---

### Post by lordfoul on 2008-11-11
I was able to get video playback working in Vlc player by changing the video output module to x11.  Hope a fix comes soon.  I'm using the mediaplayerconnectivity plugin for firefox to stream wmv, real player, and quicktime formats in x11 as well flash seems fine.

---

### Post by theApokalypsis on 2008-11-13
8.11 Released Today!

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)
[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

i will post about the flickering isssue!

---

### Post by theApokalypsis on 2008-11-13
:( appears flickering accelerated video is still aparrent with 8.11... tried some mixed settings to no avail...

good news is the 8.11 release officially supports Ubuntu, so you can run the stock installer (instead of building debs) :D

---

### Post by binbash on 2008-11-13
It is not possible to fix it till DRI2 comes, at least for ati.But you can disable flickering at videos with selecting X11 as video output

---

### Post by TVMA on 2009-01-15
I forget where I read this, but it worked for me on my lappy, ATI X1300, and my desktop  ATI HD 4850

type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under Default Output, choose X Window System (no Xv).

Boom, no reboot, don't have to restart X, just works flawlessly. I have Appearance settins on Hhigh, and no more flickering video. I stil have some issues with VLC, but Totem has no problems whatsoever.

---

### Post by nick09 on 2009-01-15
Thank you for posting that. That just fixed my flickering problems with videos on my ATI 3450.

---

### Post by threetimes on 2009-01-16
It solves the flickering, but (depending on the video) I get an extremely low framerate.

---

### Post by pelle.k on 2009-01-16
Yeah, it's a workaround. Not a fix. X11 is not using video acceleration (while xv, which do use video acceleration, has got flickering instead).

---

### Post by marcgh on 2009-01-16
Driver ATI 8.12 for ubuntu are now available.

---

### Post by marcgh on 2009-01-16
ATI has now a newer driver: 8.12
I'm using it but still compiz OR video, both together is still flickering.

---

### Post by michaelalonzo on 2009-01-17
yeah I`ve been researching alot on why my screen flickers on veoh full screen (but not on original screen) and dvd playback but not on youtube.

turned off visual effects and the flickering is gone. I also have the latest ati driver. 

still ATI is a downer

---

### Post by avaddon on 2009-02-05
It seems than ATI fixed flickering video in new 8.573 drivers, so video with compiz doesn't flickering, BUT now it's corrupted :(

---

### Post by notoriousdbp on 2009-02-06
Version 0.1 of the driver is now available.  Has anyone tried it yet?

---

### Post by markbuntu on 2009-02-06
The new 9.1 driver from ati has resolved all flickering video problems for me. I have a HD3650 running on Intrepid amd64.

---

### Post by markbuntu on 2009-02-06
I am using the 9.1 driver and have zero problems with video playback flickering in window or full screen with compiz running with totem, vlc flash, etc with my HD3650 card.
I have it running on Intrepid and Hardy. It is just great. That problem can finally be put to rest, YAY!!

You need to set the video preferences to X11 wherever you have an option to do so, turn on all the compiz workarounds and do not edit your xorg.conf. That is how my setup is configured.

---

### Post by spandanj on 2009-02-07
Reply to **markbuntu**

If you still have to use x11 in the new Catalyst 9.1, then the Problem is NOT solved because x11 does not use video acceleration, while playback in OpenGL does.

With x11 as my video playback, HD videos are slow aka frame drop due to a lack of hardware acceleration. 

So, **catalyst 9.1 has NOT solved the compiz+video flickering problem.**

---

### Post by markbuntu on 2009-02-07
Well the flickering problem is definitely solved for me. That's what I was talking about.

---

### Post by fdir on 2009-02-08
**markbuntu**, then try to run HD video or enable some filters in your player. We'll see if your CPU can do all of the job...
Newswet ATI drivers are screwed just the same way like the old one :/ :/

---

### Post by notoriousdbp on 2009-02-08
The video flickering problem is fixed for me with 9.1 BUT it only seems to work well in fullscreen mode - windowed must just looks horrible when watching a DVD in Totem.  Also, I can't successfully log out or switch user which suggests something is going wrong with GDM with this new driver.

I'm using a Radeon hd3200

---

