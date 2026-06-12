---
title: "problems with Nvidia TNT2..."
date: 2009-03-11
forum: Hardware
---

### Post by mysticaltopher on 2009-03-11
I know that the Nvidia TNT2 is not supported under Ubuntu 8.10 but I was wondering if anyone has been able to fix this problem?  The highest resolution I can get is 800x600 and I need to get 1024x768.  I've been searching the fourms and other places and have yet to find a solution to the problem....

I ran 
$sudo apt-get install nvidia-glx-71
and 
$sudo apt-get install nvidia-settings

but now I get an error on start up with the nvidia-glx-71 driver failing to install.

Do I need to remove the driver and try something else like xrandr or xorg.conf?  and if so how would I approach that?

I'm a noob and am not familiar with xorg.conf at all....Please Help!!
(the xorg.conf man file is big too, but I am trying to learn:D)
Thanks!

-mysticaltopher

---

### Post by plockery on 2009-03-22
Don't know whether this is still a problem for you. but I have had the same problem and just solved it for myself.
I am only a newbie and am using Linux Mint - a derivative of Ubuntu, but i am fairly sure the xorg.conf is the same.
You don't need to install the glx-71 package. From my experimenting that only makes things worse.

Basically all you need do in the xorg.conf is (a) specify the right driver which is "nv" not "nvidia" (b) the horizontal sync and vertical refresh figures for your monitor and (c) the resolution modes your want to see.
After I did these, Linux Mint automatically booted at the default resolution of 1024x768 and had many more options in the screen resolution preferences.

Here is what my xorg.conf looks like and the bold lines are what I added.

Section "Device"
	Identifier	"Configured Video Device"
	**Driver	"nv"**
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	[B]HorizSync	31.5-75
	VertRefresh	60-75[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	[B]DefaultColorDepth	24

	Subsection "Display"
		Depth 16
		Modes	"1024x768" "800x600"
	EndSubsection

	Subsection "Display"
		Depth 24
		Modes	"1024x768" "800x600"
	EndSubsection[/B]
EndSection

Hope this works for you too.

Peter

---

