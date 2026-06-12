---
title: "settings for touchpad on t30."
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by BlaineM on 2006-04-04
I have been trying to adjust my touchpad lately with no success.  Everytime that I have tried to adjust lines in the Xorg.conf I have had to reset the Xorg.  So I tried tpconfig, which I have not found any sufficient documentation on how to run.  Does anyone know how to set parameters with this utility?  Or has anyone else had any success at configuring the touchpad using another method?

---

### Post by BlaineM on 2006-04-05
thanks for your help and knowledge.

---

### Post by BlaineM on 2006-04-05
So again, for anyone looking for similiar help in this area. [http://www.thinkwiki.org/wiki/Tpconfig](http://www.thinkwiki.org/wiki/Tpconfig)

---

### Post by BlaineM on 2006-04-10
thanks for your help everyone.

---

### Post by mpvano on 2006-04-10
I'm not sure who you're talking to, since your messages don't seem to have any replies, but I just saw your message and thought my experience might help.

I use the following on my T-30:
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option "SHMConfig"			"true"
	Option "LeftEdge"			"1900"
	Option "RightEdge"			"5400"
	Option "TopEdge"			"1900"
	Option "BottomEdge"			"4000"
	Option "FingerLow"			"40"
	Option "FingerHigh"			"50"
	Option "MaxTapTime"			"180"
	Option "MaxTapMove"			"220"
	Option "MaxDoubleTapTime"	"180"
	Option "ClickTime"			"50"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta"	"70"
	Option "HorizScrollDelta"	"0"
	Option "MinSpeed"			"0.03"
	Option "MaxSpeed"			"0.12"
	Option "AccelFactor"		"0.03"
	Option "EdgeMotionMinZ"		"30"
	Option "EdgeMotionMaxZ"		"160"
	Option "EdgeMotionMinSpeed"	"0"
	Option "EdgeMotionMaxSpeed"	"0"
	Option "EdgeMotionUseAlways" "0"
	Option "UpDownScrolling"	"1"
	Option "TouchpadOff"		"0"
	Option "GuestMouseOff"		"0"
	Option "LockedDrags"		"0"
	Option "RTCornerButton"		"0"
	Option "RBCornerButton"		"0"
	Option "LTCornerButton"		"0"
	Option "LBCornerButton"		"0"
	Option "TapButton1"			"1"
	Option "TapButton2"			"2"
	Option "TapButton3"			"3"
	Option "CircularScrolling"	"0"
	Option "CircScrollDelta"	"0"
	Option "CircScrollTrigger"	"0"
	Option "CircularPad" 		"0"
	
EndSection

but I determined these settings and fine tune them using the command line utility called "synclient". Note that to make it work, you must at least add the line above 

Option "SHMConfig"			"true"

and restart X11 ( or reboot, if you don't know how to do that).

Then one can use the command "synclient -l" to examine all the currently available options and their values. You can also use the command "synclient" followed by a list of options as values like this:

synclient TapButton3=3 UpDownScrolling=1

with as many settings as you like per command.

You can use this to experiment with different settings.

Note also that the synclient documentation in /usr/share/doc/xorg-driver-synaptics  defines each setting.

The synclient program was automatically loaded on my T30 during the ubuntu install process. It's part of the xorg-driver-synaptics driver for the device.

hope this helps if you didn't already find it out.

Note that everything you need to know was probably alread present in the /usr/share/doc directories that correspond to installed packages. It's a good idea to hunt in there for answers when you can't figure out where else documentation lives....

Mario

---

### Post by BlaineM on 2006-04-10
Actually, I was being sarcastic with the posts, which doesn't seems to fit me all too well, being that people misunderstand my attempts regularly.  Thanks for your tips, I'll give them a try when college slows down a bit (hopefully by the end of the week)

---

### Post by BlaineM on 2006-04-11
thanks alot, the synclient was exactly what I was looking for.  Thanks for taking the time to help me with this area that I was having a problem with.  I was getting frustrated with this, and frustrated with the forums period, no one seemed to have the right answer till now.  Thanks again.

---

### Post by BlaineM on 2006-04-11
I like the settings options that I can do on the tp, but how would I get this to stay when the computer is restarted.  It seems to dump the settings when it restarts. Would I have to build a script?  Or is there another way to set this to load on boot?

---

### Post by mpvano on 2006-04-12
That's why I dumped the xorg.conf input section for you.

To make the settings stick, the easiest thing is to add them manually to x11.org. Once you've added settings for all of them, you only need to touch up any changes as you make them.

I use a baseline configuration in x11.org and refine it by adding tweaks I've made with synclient once I'm happy with them. At the moment, I rarely have to change anything at all....

You can certainly also use a script to update the full configuration (synclient can change as many settings at once as you put on its command line),

The problem with that is that if you want it to run automatically, the script needs to run after X11 starts, so the usual service interface in /etc/init.d can't be easily used. You'll need to add the script to one of the startup scripts or hooks for X11, gnome panel or nautilus.

Unfortunately, researching how to best do any of those under ubuntu was more trouble than I found it was worth. A few days of just touching up the xorg.conf file via "sudo gedit /etc/X11/xorg.conf" left me with settings I rarely need to change.

By the way, it's a good idea to keep a backup /etc/X11/xorg.conf file around so you can replace one you accidently screw up while editing it by just copying a file from the "recovery system" command line. Otherwise, you may have to learn to use (gasp!) vi to fix any typos you make that are serious enough to keep X11 from starting!

Also, don't be too hard on the forum response cycle. Most of the people here are ordinary user's just like you and I, and we only answer messages if we notice them, and if think the query is not from someone who's problems are going to be more than we can easily help with. There really aren't any official support people here looking for messages to answer. This isn't an official support mechanism for ubuntu.

good luck,

Mario

---

### Post by BlaineM on 2006-04-12
thanks for all your help.  I played around with the settings for the touchpad in the xorg.  I found settings that I am quite happy with.  Thanks again for your assistance.

---

### Post by BlaineM on 2006-04-12
Also I was wondering if you have in your t30 the Radeon 7500 mobility, and how it runs for you.  I guess that the only thing that I have to compare it to is my 9800 pro in my tower running Ubuntu which runs great.  Does it seem like slightly weak to you?  And the xorg does not post that right name, is this a wrong driver, or just posted wrong in the xorg?

---

### Post by mpvano on 2006-04-12
I have the Radeon 7500 and I find it's performance adequate for my use. I don't really do much where video performance is a problem. It's not noticeably sluggish or anything.

I do believe that the driver is buggy, however. There seem to be some problems with the variable clock power saving features. My machine seems more prone to freezing when coming out of sleep if DynamicClocks is enabled. It appears that if it's not enabled however, the standby power drain rises enormously causing short battery life in sleep. (10-12 hours max).

I still experience occasional lockup on resume even if DynamicClocks is off, but I think the whole sleep/suspend/hibernate thing may not be all that stable in Breezy yet, so I'm living with the problem. Fortunately the journalled file system seems to recover from crashes easily.

The radeon seems to work best at full resolution, the radeon does buffering and downsampling to run at less than the native 1400x1050 in this particular T30 and I think it seems to slow it down a little. Unfortunately, I usually find resolutions above 1152x864 to be a little hard to read at my age.....

I don't see any noticeable delays in scrolling or paging data at any resolution, but as I said, I don't do anything like games or real time video with this machine. The closes to animation I care about is VU meter's etc. in audio software and they seem quite responsive.

I'm quite pleased with ubuntu on this T30 except for the occasional (1 time in 20 or so) resume failures. It also took me a while to get all my complicated networking needs sorted out so that it was convenient to use, (I did have to build my own configuration switching solution)  but I think the whole wireless industry is going throuh growing pains right now (including my Windows systems), so I'm sure we'll get that sorted out. Almost everyone's wireless drivers and utilities are currently having trouble in environments where multiple networks overlap, especially of some of them are on the same channels.

It also took a while for me to figure out how to configure the keyboard properly (the Thinkpad wiki has been an invaluable resource, but you must take everyting there with a grain of salt). These things all seem to go with the territory when dealing with new Linux releases.

For what it's worth, I've found similar problems in the XP drivers for a number of devices. Right now, for example, my wireless connections are more predictable and reliable in linux than under IBM's connection manager in XP.

I work on a lot of machines running almost all common operating systems and own quite a few different kinds here, but this T30 under Ubuntu is my "home base" where all the master copies of my projects and data files exist and I'm pleased with the way it's currently working.

hope this info helps,

Mario

---

### Post by BlaineM on 2007-10-18
thanks alot for the feedback.  I now am in the process of trying to find a new laptop, and consolidate all of the different machines that I run into one.  1. desktop 2. laptop 3. server -- The T30 has been the first laptop that I have owned that did not give me any problems over the life that I have had it.

Of course general maintenance like changing a failed hard drive, and changing out some bad ram are normals with any machine that gets used everyday.  This has been the first laptop that I have loved to run.  And all of the documentation on getting the T30 optimized to exactly how I want it to function are highly available.

Blaine

---

