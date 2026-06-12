---
title: "Dual Monitor Issue in Karmic with Intel Card on Laptop"
date: 2010-01-13
forum: Hardware
---

### Post by Lateralis on 2010-01-13
Hi all. 

I posted this problem last year when I upgraded to Karmic from Jaunty.  I have tried everything that I know but nothing I've done has fixed what is for me a very frustrating problem.

I have a laptop which uses the Intel HD 4500 graphics card.  

```

$ lspci -v 

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Fujitsu Technology Solutions Device 1139
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f8000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [d0] Power Management version 3
	Kernel driver in use: i915
	Kernel modules: i915

```

The laptop has a 13" laptop display with a DVI output.  In Jaunty I was able to connect up an external monitor to it just fine.  I was able to select from the Display GUI the correct refresh rate and the correct resolution.  There were oodles of possibilities as well.  After the upgrade, the laptop screen is fine but no external monitor I have tried (3) has worked properly.  The most recent attempt with a Dell monitor has proved to be as frustrating as the others.  There are virtually no options in the Display GUI anymore - there are just 5 resolutions and just 60 Hz refresh rate listed for the external monitor.  None of the resolutions are appropriate, with most of them being non 4:3 aspect ratios (which is the aspect ratio of the external monitor).  

I have tried reconfiguring Xorg.conf using the following:

```

sudo /etc/init.d/gdm stop
Xorg -configure

```


I have tried editing Xorg.conf but I'm not that skilled at it.  Nothing I've tried has worked.  

My xorg.conf currently looks like:

```


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "dri2"
	Load  "dbe"
	Load  "glx"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
                Virtual 2562 1024
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
                Virtual 2562 1024
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
                Virtual 2562 1024
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
                Virtual 2562 1024
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
                Virtual 2562 1024
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Virtual 2562 1024
	EndSubSection
EndSection

```

I really am at my wits end.  I need 2 monitors for my work so this is a BIG deal for me.  What is particularly frustrating is that dual monitors worked perfectly fine under Jaunty 9.04 and I cannot fathom how it has been broken.  

So really, any help and advice would be hugely appreciated.

---

### Post by Lateralis on 2010-01-20
Anybody?  

This problem has been bugging me for 3 months now and I don't know how to solve it. 

I've submitted a bug report to Launchpad, but I do kinda need this second monitor working...  Any work around solution would be gratefully received.

---

### Post by pyjamashark on 2010-01-24
Did you ever solve this issue? ...have the exactly the same thing bugging me.
Grrrr

---

### Post by Lateralis on 2010-01-25
I would love to say yes, but unfortunately, no.  The problem still exists and I am totally our of ideas. 

I have submitted a bug report to Launchpad using the Test Hardware facility in Ubuntu, but so far nothing.  There are other similar bug reports on Launchpad but I am afraid to say that a lot of them are sitting there with little activity.  Either no one can be bothered to investigate the problem or the problem is sufficiently complex that no one knows how to fix it.  Either way, it is both troubling and frustrating in the extreme.  

I have tried many of the "solutions" that appeared to work for other people, ranging from using metacity instead of compiz and turning off all compositioning tools all together.  I've updated everything I possibly can, I've tinkered with Xorg (and generated a new xorg.conf using built in scripts after switching off the gdm and falling back to a shell-only environment), probed and prodded and poked and tweaked.  Nothing I've done seems to work.  

It should perhaps be pointed out again that I am an absolute n00bie when it comes to the GDM, xorg and the like, so I may have missed something quite fundamental and basic to try.  However,

a) I've never *had* to fiddle with Xorg to get anything to work in the past, much less dual monitors and
b) I've set the virtual screen size to be sufficiently large to enable the two monitors to run at their maximum nativ resolutions.  

I have tried to change xorg.conf such that it lists the correct resoltions and frequencies for my external monitor, but that failed as well.  Again, I don't now if that is because I'm a n00bie or whether it is because Karmic just flatly refuses to co-operate.  

I am considering downgrading back to Jaunty, as I know that the monitor was picked up and supported fine.  But this for me is the most irritating part of all - support for a second monitor was absolutely fine in previous versions of Ubuntu and not ONCE have I encountered so much as a whiff of a problem, much less a show-stopping one like this.  

I am going to wait for Lucid to come out in the hope that a fix is found and the next update fixes the problem.  If it doesn't, then I fear that I may switch allegiance to Debian or another flavour of Linux.  It seems like an extreme reaction to what many might consider a minor issue, but I do need a second monitor at work for productivity reasons (and this year I *need* to be highly productive if I want to get my PhD...) and the many breakages (udev, sound cards, dual monitors among other things) in the last version of Ubuntu has left me feeling quite disenchanted.  Whilst I do appreciate the enormous effect that went into Karmic to make it look swish and stylish, as well as updating a lot of the backend code,  but what is the point in large changes if important things get broken as a result?  One step forwards but two steps backwards isn't the key to progress!  And ultimately I am only after a stable operating system that works day in day out without any issues or complications; Ubuntu was that operating system but right now it isn't.  And that does make me greatly sad on the inside.

---

### Post by Sky Aisling on 2010-03-14
I'm attempting to help a friend out with a similar dual monitor setup situation.  The laptop aspect ratio is 16:09.  The external monitor ratio is 4:3.  The laptop is using Ubuntu Netbook Remix 9.10.  So far, the answer has eluded us.  I will check back to your question when/if we find the solution.  Keep the faith.  The answer is out there.

---

### Post by efflandt on 2010-03-14
Just curious if the external display shows nothing at all during boot if the monitor is on (and that input is selected if an HDTV) before booting?  Does /var/log/Xorg.0.log or **xrandr** command show any info about the DVI connection?  Note that if you connect a monitor after booting, you may need to log out of X and back in before it would appear.

Are you sure that you have the proper type of DVI cable? DVI can do digital (like HDMI) or analog (like VGA) with different cables or adapters, but the display might be expecting digital.

When I boot my laptop with older Intel 945 VGA and 1280x800 laptop screen connected to HDTV, BIOS immediately switches to just the external display at 720p during boot, and then both displays for the Ubuntu logo and login prompt.  But the login prompt and X default to a common 1024x768 mode for both displays, and it does not automatically offer any widescreen that works for the external display.  The 1280x720 mode it offers is overscanned (maybe due to 1280x800 laptop screen).  So I use **xrandr** commands in a script to set the proper native mode and turn off my laptop screen when connected an external display.

DVI or HDMI should be more automatic, since they communicate their capabilities more completely to the video source.  But you may need to disable "splash" as a kernel boot parameter, because I have had that cause boot to hang (after grub menu) when switching DVI monitors with different native resolutions (even if capable of accepting the resolution in /etc/usplash.conf).

I don't have DVI or HDMI on a laptop.  But other than the spash boot issue, X automatically recognized the native resolution of anything DVI connected to my desktop, 1280x1024, then 1280x720 older HDTV, then DVI to HDMI 1080p HDTV.

---

### Post by Sky Aisling on 2010-03-14
Good Morning Efflandt,

I just picked up your reply.  I'm on my way out the door for a while.  I'll respond later.  Our situation has just come about and we digging into the details now.

---

### Post by Lateralis on 2010-03-15
To give an update on my problem, I have updated to Lucid Beta 2 a few weeks back (currently Beta 3 I think) and there has been *some* progress on the dual monitor front but the problem still exists.  

There have been many updates to the Intel driver modules and I now have a few more resolutions I can select for the external monitor, but the correct resolution is still not available.  

Strike through part of that last paragraph - I have just checked and I now have fewer resolution options after the latest Intel update than I had before.  The available resolutions are the same as those I quote previously. 

Thus, the problem still exists and no changes have been seen after my upgrade to Lucid. As such, I'm still at a loss.  


@ efflandt


To provide a few more details...  I have tried two external monitors: a Video7 19" and a Dell 19".  Both support resolutions up to 1280x1024.  I was using the Video7 quite happily under Jaunty without any issues or problems *whatsoever*.  Everything *just* worked, *exactly* as it should do.  I cannot stress this enough.  

I always used to boot up into Ubuntu with the monitor disconnected then once I was logged in I would plug in the external monitor.  This is because the BIOS would switch off the laptop monitor and display everything (POST and GRUB menu) on the external monitor only.  For reasons of personal choice I decided I didn't like that so would always connect the monitor up afterwards.  

This should also be the way that it should work.  Remember, this is a laptop.  The whole point of a laptop (well, mine at least) is that it is portable so that I can be in the office one minute then in the lab the next.  Plugging and unplugging a monitor on the fly is to be expected *and it did once work fine*.  Moreover, when I give presentations at conferences and within the department it is necessary to connect the laptop up to a projector.  In these situations the project will be connected up to the laptop after Ubuntu has been loaded.  Only getting a working resolution when the external device is connected prior to booting is entirely unsatisfactory. 

Now, I have been at pains to point out in multiple different threads on multiple different occasions that this worked flawlessly and I encountered no issues of any kind whilst I ran Jaunty.  My upgrade from Jaunty to Karmic broke this happy tranquillity and I have spent 6 months trying to fix this problem.  Nothing I have done has sorted it out, no one has been able to come up with a solution and no updates to the Intel kernel module or to Xorg has fixed the problem and, as it stands at the moment, the problem has not been resolved in Lucid.  


So this leads me to comment on a few of your suggestions.  Firstly, the Video7 monitor only accepts VGA.  The output from my laptop is DVI, but I have a DVI adaptor which plugs into a VGA cable.  This combination worked *perfectly* under Jaunty.  As such, the hardware is not at fault.  

The Dell monitor can support both DVI and VGA.  As I have a VGA cable that is the one that I am using.  There are no spare DVI cables around at work so am unable to change the cable, although I have a spare one at home which I have been meaning to try for a few weeks.  But again I am at pains to stress that the setup I described worked fine in Jaunty without hiccup.  

Secondly, splash is enabled in my grub menu but I've never, ever, ever, under any version of Ubuntu in the last 3 years on all of the PCs that I have used encountered a problem where I've had to turn that off.  


So, the fact still remains: everything was fine in Jaunty but the upgrade to Karmic broke my dual monitor support.  Something was either upgraded, replaced or deleted during the update which has meant that I can no longer use an external monitor with my laptop.

---

### Post by RealNitro on 2010-03-22
Try a 4:3 external monitor. I've been having the same issues with my Acer 5630 (Intel graphics). I just tested the Lucid beta 1 live dvd, and I still have the same issue.

---

### Post by Lateralis on 2010-03-22
I** am **using a 4:3 aspect ratio external monitor...

And to reiterate, the laptop is running what I believe is now the third beta of Lucid.  Same problem, but there are updates to both Xorg and Intel almost daily (certainly weekly).  So I'm still hopeful...

---

### Post by Contra75 on 2010-03-30
I also have an issue with Ubuntu 9.10 on my Dell laptop with Intel on-board graphics not seeing the second monitor (which is actually my HDTV), or rather is sees that there is another monitor, but there is no output to it no matter the resolution I indicate for it in the Display settings. 
Very disappointed. Win XP just works w/o any issues on the same laptop.

---

