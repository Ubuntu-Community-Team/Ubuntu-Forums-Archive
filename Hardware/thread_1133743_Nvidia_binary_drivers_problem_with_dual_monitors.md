---
title: "Nvidia binary drivers problem with dual monitors"
date: 2009-04-23
forum: Hardware
---

### Post by novice buntu on 2009-04-23
Hi,

Dell Precision T4500; nvida Quadro FX 570, Ubuntu 8.10, 2.6.27-11-generic

I have cocked up my machine and need some help if anyone can.

All was well, after the initial install my 2 monitors worked fine. I had a huge desktop spanning both. 

Months later I wanted to rotate one of the monitors so it looked more portrait than landscape - 1200 x 1920 as opposed to the usual 1920 wide and 1200 height. I saw an article on how to do this and it referred me to the Binary Hardware drivers install at

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I could not get the divers to activate. I have got all the necessary headers installed but it just didn't happen. I think at this point I need to 'fess up and say I installed the Nvida linux drivers as well. I did re-install my kernel and headers to try and remove the Nvidia or anything else I might have cocked up. 

The bottom line is now my machine doesn't see both monitors, it just mirrors them. I still can't get the drivers to activate despite my best efforts. I'd just like to get back to my old config. 

Here's the current x11.conf which I know is missing a stuff.

Section "Monitor"
	[INDENT]Identifier	"Configured Monitor"[/INDENT]
EndSection

Section "Screen"
	[INDENT]Identifier	"Default Screen"[/INDENT]
	[INDENT]Monitor		"Configured Monitor"[/INDENT]
	[INDENT]Device		"Configured Video Device"[/INDENT]
	[INDENT]SubSection "Display"[/INDENT]
		[INDENT][INDENT]Virtual	3840 1200[/INDENT][/INDENT]
	[INDENT]EndSubSection[/INDENT]
EndSection

Section "Device"
	[INDENT]Identifier	"Configured Video Device"[/INDENT]
EndSection


Is there some routine/apps I can run that might sort this problem out. I'm pretty green with X11, I think there should be another screen/monitor in the conf above but I'm not sure how and he back-ups are not telling me much.

Any help will be much appreciated.
Thanx.
Dp.

---

