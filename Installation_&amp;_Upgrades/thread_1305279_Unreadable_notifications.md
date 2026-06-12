---
title: "Unreadable notifications"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by plantboy1 on 2009-10-29
I upgraded my system today and I haven't had any real issues other than Ubuntu One and my notifications.  The Ubuntu One issue I read is a bug that will be fixed.

The notifications, however, are a major issue.  The box for the notification pops up but all it shows is a mass of lines and is completely unreadable/unseeable.

Is there any way I can fix this quickly?  I never knew how much I relied on notifications until now.  I'm on a ThinkPad A31.

---

### Post by cyruses on 2009-10-30
Hi, I just upgraded my Jaunty Jackalope install to Karmic Koala. Everything is running fine except for one thing. At random times, I get a green or pink rectangle underneath the date and time. Whenever I move my cursor to the box it disappears, however when I move my cursor away it reappears. Sometimes it goes away by itself but it's annoying. I've also included a picture.

My computer is an IBM Thinkpad A31, Pentium 4 mobile processor, 1Gb of RAM, ATI Mobility Radeon 7500, 80GB HD. 9 year old machine.

---

### Post by issih on 2009-10-30
I'm pretty certain that is a screwed up version of the notification system. Normally it pops up little messages about new emails, system events, volume levels, the song playing etc.

It should be a sort of translucent black with white writing, but the rest of the behaviour is exactly what it is designed to do:

[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

I am not sure why you are getting a garbled version of it, but I'd presume its a problem with the graphics drivers in some way.

---

### Post by cyruses on 2009-10-31
> **issih said:**
> I'm pretty certain that is a screwed up version of the notification system. Normally it pops up little messages about new emails, system events, volume levels, the song playing etc.

It should be a sort of translucent black with white writing, but the rest of the behaviour is exactly what it is designed to do:

[https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD)

I am not sure why you are getting a garbled version of it, but I'd presume its a problem with the graphics drivers in some way.

Yeah it's probably the notification system, because in rhythmbox as soon as a new song starts playing the box comes up. Before I had my visual settings on none, now I brought it up a notch and the notifications are fixed, but at the bottom right above the bottom panel there's a red line for some reason, and it's not my background. Attachment included. Same thing happens when I right click, around the options there are odd colors like red and green.

---

### Post by issih on 2009-10-31
I'm fairly certain you are having graphics driver issues.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I think that is the driver that the system should be using, so have a little browse and see if anything jumps out at you.

I'm afraid I can't really be more useful as I don't have anything that runs an ati card except for one with an HD2350 in it, which runs under the proprietary drivers - which you can't use.

---

### Post by plantboy1 on 2009-11-01
Bump

---

### Post by macogw on 2009-11-01
What sort of lines? Crisscrossing? Stripes?

---

### Post by issih on 2009-11-01
I've no idea if a solution was found, but this thread is about the exact same issue - on the same machine:

[http://ubuntuforums.org/showthread.php?t=1305987](http://ubuntuforums.org/showthread.php?t=1305987)


so its not just you - I still haven't got any good advice other than to look into the graphics drivers though..

---

### Post by spacecheck on 2009-11-02
I was having the same problem getting these notifications to appear correctly and was also unable to get the System Monitor to display properly.  As I had the problem with System Monitor first, I had been looking for a solution to that and saw the problem listed in lauchpad:  [https://answers.launchpad.net/ubuntu/+question/87625](https://answers.launchpad.net/ubuntu/+question/87625)  The cited resolution involved turning on "Normal" on the "Visual Effects" Tab under the Menu item: System\Preferences\Appearance instead of "None".  I tried that and it resolved both System Monitor AND Notification problems on an IBM TP T40.  Under 9.04, the option "None" was previously & effectively used, with no such display errors.  I (and apparently others, considering there are several forum messages about it) would certainly appreciate it, if the problem could be resolved without having to waste valuable resources required for silly "visual effects". No 'visual effects' were needed to use the System Monitor or see system notices in past releases and I see no need to have to use them now.

---

### Post by issih on 2009-11-02
well, you could try turning the special effects back to none, but enabling compositing in metacity, and see if that helps..

"Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing! "

you'll still be using a few more resources, and you'll get a tiny smattering of eye candy, but its much less than with compiz, and you never know, it might work :s

Hope that helps

---

### Post by berilac on 2009-11-02
I am experiencing exact same problem.

Running Karmic on Thinkpad A31.

Notifications appear as black area, broken up by kind of fuzzy horizontal white line sections (best description i can give currently).

Same thing happens to whole window of system monitor when that is run as well (Haven't seen it in other apps as of yet).

Finally, on trying to enable compositing in metacity, the whole screen produces the same effect and nothing is readable...so it is definitely compositing issue.

For the record, this is the output from compiz-check:

> 
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check: line 488: [: 1810: binary operator expected
           [ OK ]


Any ideas? or questions?

Thanks!

---

### Post by plantboy1 on 2009-11-02
I haven't been able to get online for a bit, but that's the exact thing I was describing.

Likewise, enabling compositing in Metacity does make things worse.

I've found that (going by the previous post) that compiz *does* work on the ThinkPad A31 that I'm on but since the upgrade to 9.10 I needed to disable it because it doesn't work.  Everything used to pre-9.10.

I figure it's a driver issue like someone else said earlier, but I don't know what I can do about that, but I'm taking a look at the link someone else posted and I'll post back if I find anything useful.

---

### Post by plantboy1 on 2009-11-02
Okay, the output of "lspci -nn | grep VGA" gives me 

> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]


Which is supported for full 3D. (the ThinkPad A31 graphics card is in the 7500 / rv200 based cards.)

There's apparently known issues with it as found here: [https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI]("https://help.ubuntu.com/community/Radeon_9200/9250_%28RV280%29_and_DVI")

I would try what's suggested on the page (though it is for older Ubuntu versions, I figure it might help) but I NEED a working system and so I'm not going to try it until I know it's not going to break anything.

**EDIT:** I disabled compiz after I upgrade since it was giving me problems, but now it seems that I can't re-enable it.  I get a "searching for available drivers" thing then an error saying that desktop effects could not be enabled.

---

### Post by Sunflower1970 on 2009-11-02
I'm having a similar problem with a Thinkpad R40. Has an ATI Radeon 7500 M6 LY card in it. 

I know that compiz works since I've been able to use it in the past. (I just did a fresh install from 8.10--and it was perfect)

When I turn off the Effects in 'Appearances', my notification system is similar to that above--and a lot of other wonky problems appear.

But, I just ran into an odd workaround. 

I saved my xorg.conf from 8.10, and had set it up to use with 9.10. Here's the code:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "AGPMode" "4" 
	Option "AGPSize" "64"
	Option "RingSize" "8"
	Option "BufferSize" "2"
	Option "EnablePageFlip" "true"
	Option "EnableDepthMoves" "true"
	Option "RenderAccel" "true"
	# Eyecandy Stuff
	Option "AccelMethod" "4"
	Option "EnablePageFlip" "true
	Option "DDCMode"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"
EndSection

```

It sort of worked, using the 'Effects' in 'Appearances', but I had weird lines across the top of the screen--kind of like TV snow. And it was *only* on the desktop wallpaper. It wasn't in the taskbar, or in any new window I opened up. 

When I turned the graphics completely off, I'd have all sorts of weird problems, so they have to be on. 

So. Instead of the 'Extra Effects' option under 'Appearances' I chose the 'Normal', and also this:
> written by issih:

"Open the GNOME Configuration Editor; press Alt-F2 to open the Run Application dialog and type gconf-editor. Click Run. Navigate to Apps->metacity->general. Check the compositing_manager box, and Metacity will immediately restart with compositing! "

And it seems all the odd lines go away. I've set up some extra effects in the compiz manager--just no cube--and so far so good. Everything's holding. 

I haven't tried to reboot yet and see if the problems go away, but so far, it looks like everything might be okay...

ETA:

Darn. I just rebooted. Same thing. Lines across the top *only* on the desktop wallpaper. Nowhere else. 

Oh, and my volume and mute buttons no longer work, as they did in 8.10

I give up. I may try 9.04 and see how that works out.

---

### Post by plantboy1 on 2009-11-02
I gave that a try but it didn't help me at all with my notification issues, so I don't know.

---

### Post by spacecheck on 2009-11-03
> **plantboy1 said:**
> I gave that a try but it didn't help me at all with my notification issues, so I don't know.

 Did you even try turning on "Normal" effects on the "Visual Effects" Tab under the Menu item: System\Preferences\Appearance instead of "None"?  This resolved the problem on a IBM T40 (with the same graphic card).  WE know it is stupid to waste CPU & graphic resources on animated "fading" menus & transparent 'windows', etc., but the developers may have forgotten it. Perhaps they'll remember, & revert to a 9.04 compiz policy, where notices & system monitor worked fine with no "effects" enabled.  Ciao

---

### Post by carolinason on 2009-11-03
sort of the same problem here. bottom line is compiz is broken and you know this isn't going to get fixed! and i was looking forward to this release. back to 9.04 i guess...

this was the first ubuntu release that the alphas and beta where extremely buggy. i think ubuntu is losing it's charm. but i must admit the last release was excellent. i'm wondering if i should simply go back to debian. the reason i say that is... bugs like this just don't get fixed in ubuntu. my graphics card is an established open source supported card. this should not be an issue. and it seems every other release there is a graphics problem!

---

### Post by dankoc on 2009-11-03
I am also having the same problem -- an old Thinkpad X31 w/ Mobility Radeon M6.

# lspci| grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

I have turned off all visual effects, so the only place that it shows up for me (that I have noticed thus far)is notifications.  Just for kicks, I tried rolling notify-osd package back to the 9.04 version manually -- same problem.

---

### Post by dankoc on 2009-11-04
Hi, All,

I have gotten everything working pretty well on my system by switching to fglrx drivers.

My system is a Thinkpad X31 with Mobility Radeon M6.  Of course, you may have less luck depending on your specific graphics card and system.
# lspci| grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

To get fglrx installed, I followed the instructions here:
[http://swiss.ubuntuforums.org/showthread.php?t=899178](http://swiss.ubuntuforums.org/showthread.php?t=899178)

Note that those instructions are for an earlier version of Ubuntu.

Nevertheless, I followed them pretty closely up through step 8 (I used the using the entire xorg.conf file that is pasted into that page without any changes).  

After step 8, I did NOT reinstall compiz -- I just set visual effects to Normal in System/ Preferences/ Appearance/ Visual Effects menu. 

After that, everything works fine!  I would say that its actually running pretty well now.  Saves me the time that it would take to reinstall 9.04!  Yay!

Good luck!

---

### Post by plantboy1 on 2009-11-04
I have the M7 so I don't know if that would help me, though it might.

I need to know if it works for my system because I need a working computer for school and if I kill this one I'm screwed...and my luck with messing with drivers seems to always leave me needing to reinstall.

---

### Post by tormod on 2009-11-05
This is [https://bugs.launchpad.net/bugs/426582](https://bugs.launchpad.net/bugs/426582)

Please also see [http://ubuntuforums.org/showpost.php?p=8221972&postcount=6](http://ubuntuforums.org/showpost.php?p=8221972&postcount=6)

---

### Post by bigturkey on 2009-11-09
Solved!

The previous reply was very helpful.

Here's how I got it working on my thinkpad X31

Basically create a /etc/X11/xorg.conf

...as follows:

```
Section "Device"
       Identifier "m6-radeon"
       Driver "radeon"

       # Enabling EXA fixes the notifications
       Option "RenderAccel" "false"
       Option "AccelMethod" "EXA"

       # Xorg will gobble CPU unless you add...
       Option "MigrationHeuristic" "greedy"
EndSection

Section "Screen"
       Identifier "laptop-panel"
       Device "m6-radeon"
       DefaultColorDepth 24
       SubSection "Display"
           Depth   1
           Modes "1024x768"
           #Virtual 1024 768
       EndSubSection
EndSection

Section "Extensions"
        # I don't use the compositing settings, so off!
        Option "Composite" "Disable"
EndSection

```


You should be able to get away with only the Device section.

- rich

---

### Post by smatofu on 2009-11-10
I would like to confirm that this fix works in Ubuntu 9.10 on IBM ThinkPad R40. Thanks a lot!

---

### Post by plantboy1 on 2009-12-01
I can confirm it works on the IBM ThinkPad A31 for fixing the notifications (Ubuntu 9.10)

---

### Post by cineojo on 2009-12-14
Hi! Unreadable notifications now seems to work (IBM R40). But i'm still experiencing some problems with video display. Google earth crashes... And Hugin panorama creator, too. 

this is how Xorg.conf looks like:
Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Option		"AccelMethod" "EXA"
	Option 		"EnablePageFlip" "1"
	Option		"DynamicPM" "on"
	Option 		"FBTexPercent" "32"
	Option 		"AGPFastWrite" "on"
	Option 		"AccelDFS" "on"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Defaultdepth	16
	Virtual		1024 768
EndSection

---

### Post by tormod on 2009-12-14
Any use of AGPFastWrite is doomed to fail. Please see the radeon man page or the warnings in your Xorg.0.log.

---

