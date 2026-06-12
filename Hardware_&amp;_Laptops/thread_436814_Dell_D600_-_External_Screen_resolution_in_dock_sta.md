---
title: "Dell D600 - External Screen resolution in dock station + fan problem"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by mAIJK on 2007-05-08
Hello.* This problems is in Ubuntu 7.04*

**Problem 1.**
I have a DELL D600 with Dock station connected to a AOC 18" LCD display that is capable up to 1280x1024.
My laptop screen is capable up to 1024x768.

I have a Radeon 9000. I use standard drivers to graphic card. 

I want to be able to use 1028x1024 when I connect my computer to the LCD display (connected to dock station) with lid closed. And when I use only laptop I want to use 1024x768.

I only have one screen in my Xconfigt with modes "1024x768". I tried to add "1280x1024" their but I can only choose 1024x768 when I use the "Screen Resolution" tool in Ubuntu.

Anyone who have any ideas about this? Doesn't Ubuntu find my external screen because it only have one "Screen" section? When I connect my external screen through the dock station I get the "picture" on the external and my lappy screen gets all black, thats no problem cuz Im working on my external. But the resolution 1024x768 is not very fun to work with.

**Problem 2.**
When running Ubuntu on my lappy the fan sound abit all the time. But when Im working in Windows XP the computer is totaly quiet. The fan doesn't blow alot in Ubuntu but I think it strange that it blows anything when It's quiet in Windows XP.

I would be very glad if you could help me with this, I have tried to find som information about this but everytime I try I make X crash :P

Best Regards
Mikke

---

### Post by mAIJK on 2007-05-09
Sorry for bumping but doesn't anyone have a clue? :)

---

### Post by Roscoe on 2007-05-09
Same Issues here.

Conncting to external monitor via DVI.

---

### Post by mAIJK on 2007-05-10
> **Roscoe said:**
> Same Issues here.

Conncting to external monitor via DVI.

Yeah. All information I find about Dell D600 and this problem is that it is, a problem. Can't seem to find any solution. Maybe there is one. What I don't understand is why I cant change to 1280x1024 when I have added modes "1280x1024"....
Strange...


Hopefully someone wise will answere, I would be so glad:)

---

### Post by mAIJK on 2007-05-10
Here is my Screen. Why cant I change to 1280x1024? I have added the Modes as you can see:


[I]Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection[/I]

---

### Post by mAIJK on 2007-05-15
Finally I solved my problem. Now I got one desktop for each monitor. Perfect! Cause when I disconnect my external monitor I still can work at my lappy. PERFECT!

Here is my config file, maybe someone else wants it :)

[I][SIZE="2"]Section "Device"
Identifier "0 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
Option "MonitorLayout" "LVDS,TMDS"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"
Identifier "1 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
Option "MonitorLayout" "LVDS,TMDS"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Monitor"
Identifier "Primary Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Monitor"
Identifier "Secondary Monitor"
Option "DPMS"
Modeline "1280x1024" 109.62 1280 1336 1472 1720 1024 1024 1026 1062
EndSection

Section "Screen"
Identifier "Laptop Screen"
Device "0 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Primary Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "LCD Screen"
Device "1 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Secondary Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

#Section "ServerFlags"
# Option "Xinerama" "true"
#EndSection 

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Laptop Screen"
Screen 1 "LCD Screen" LeftOf "Laptop Screen" 
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection [/SIZE][/I]

---

### Post by huygens on 2007-05-16
I have no solution to your problem. This seem to be a problem in the ATI driver (the restricted one) :-(
I haven't try it with the open source one, though that the one I'm using now as it is much more stable (I mean for the Radeon Mobility 9000)

For information on Dell Latitude D600 with Ubuntu, there is a wiki page: [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD600](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD600)


As for the CPU making some noise. My D600 is much more quiet under Ubuntu than under Windows (due to a heavy corporate - read mandatory/obliged - anti-virus and heavy swapping ! do not ask me why windows swap so much whereas I do not have the problem under Linux, because I have no clue!) So this means you have a process that is eating your precious CPU.
Try to check that CPU throttling (lower the CPU frequency for lower energy consumption) is working and that the CPU is idle most of the time. You could use some Gnome applet for that: right click with your mouse on the Gnome top bar and select "Add to panel". Search for "CPU frequency scaling monitor" and "System monitor", add them both. You should verify that they are most of the time at the "lowest" level, which means respectively one or two green level out of the 4-5 and mostly black (really few blue colour).
If it is not the case, launch System->Administrations->System monitor. Go the the "Processes" tab and sort by "% CPU". See which process is continuously consuming CPU (apart gnome-system-monitor process)

---

### Post by xflbret on 2007-05-17
majik, I also own a latitude d600 which also has the ati mobility radeon that no one can seem to write good drivers for. it has been an absolute nightmare trying to get this to work correctly. would you be willing to post step-by-step instructions, alone with your complete xorg.conf file? i tried copying and pasting what you posted, but my lappy doesn't like it.

i would be so so grateful for any help. thank you.

oh, ps, did you ever get beryl running on yours?

---

### Post by xflbret on 2007-05-18
please?

---

### Post by mAIJK on 2007-05-18
Hello again.

Well, I have tried the orginal ati drivers that were installed directly after installation of Ubuntu. I now run on the MESA drivers "radeon".

I have two solutions, neither of them are 100%.

First solution for dual screens with external desktop resolution bigger than 1024x768 works REALLY nice. When I run without my external desktop I can work on my lappy scren, When I plug it in I can use both. I have one desktop on each screen. I do not use XINEVIEW cuz It's better to have one desktop on each monitor. I dont use the lappy monitor so much when my external screen is connected. The problem with this config is that Direct Rendering doesn't work correct. That means that games and Beryl doesn't run propertly.

The other solution Is that I use an other config and close my laptop lid. When I run that config direct rendering is working lika a dream and both Beryl and games run smooth. The problem with this config is that I can't seem to get bigger resolution then 1024x768 on my external screen. I have tried to add Modes 1280x1024 but It doesn't work.

So I change config and restart when I want to play. I don't care so much for Beryl or desktop effect anymore. Usually I run on my first config there I get on desktop on each monitor. This is good if you don't want to play or use beryl. I would run on my other config all the time If it was possible to get higher resolution on that one.


Sure, I can make a step-to-step guide. I am at my work now so I can't help you right now! But hang in there and I will help you soon. 

But, no one of these configs are the best. The best would be if I could get direct rendering to work on my first config. Butt it wont. I have tried different drivers :/ It seems that direct rendering only works if i DON'T use the laptop monitor...

Which solution do you want?

---

### Post by mAIJK on 2007-05-18
ps. In my config that I have pasted I use the standard ati driver. I don't use that one anymore. Running mesa drivers "radeon" now.

---

### Post by xflbret on 2007-05-19
any progress on getting that xorg.conf posted?

---

### Post by xflbret on 2007-05-19
what i would love is to run beryl on 7.04, and to habe 1024 resolution. what i would also love is to have to identical desktops, so i can use my laptops for presentations and use it with my kvm swtich at work

---

### Post by xflbret on 2007-05-20
i edited my xorg.conf file and insterted all the sections majik posted, yet whenever i try to take the resolution down to 1280 its like i didnt do anything at all...the screen goes black for a few seconds, then reverts back to the original 1400 resolution. .what gives?

---

### Post by xflbret on 2007-05-21
???

---

### Post by xflbret on 2007-05-23
uh, hello? I believe there was mention of forthcoming info. I could really use it.

---

### Post by xflbret on 2007-05-23
I really think this majok guy is yankin our chain. He hasn't responded lately, and I have tried the sections in my xorg.conf file that he claimed worked for him, and they just don't work. They just don't. There's no way to sugar coat that

---

### Post by semreh on 2007-05-24
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/xorg/+bug/68212](https://launchpad.net/ubuntu/+source/xorg/+bug/68212) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The following other two threads look as through they are the same problem as well.  No solutions. :(

[http://ubuntuforums.org/showthread.php?t=422810]("http://ubuntuforums.org/showthread.php?t=422810")

[http://ubuntuforums.org/showthread.php?t=392425]("http://ubuntuforums.org/showthread.php?t=392425")

semreh

---

### Post by FerhatBingol on 2007-05-29
Can the problem be a Video BISO default values?

try finding information about the software "915resolutions"

---

### Post by HieroPosche on 2007-05-30
I"m using a d600 as well, haven't really messed with graphics and drivers as I'm new to linux and I'm still feeling my around simple tasks. :P

But as for the fan issue, I've had so many issues with my laptop and cooling, at one point I had a freezer full of ice packs so I could keep switching them out every half hour under my laptop so could keep playing wow without the cpu going crazy lol.  Other than cleaning and regreasing the heat sink, my best solution was to run a great program that can be found here: 

[http://www.diefer.de/i8kfan/index.html](http://www.diefer.de/i8kfan/index.html)

This is a somewhat sketchy program in that it will void your warranty if you still have one, but it basically gives you total control over your fan system.  Speeds, high and low temp points, and a nice little taskbar cpu temp gauge.

As far as I know it's a windows only program, but maybe someone can get it going for ubuntu cus I'd like to be able to use it again :)

---

