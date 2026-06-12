---
title: "Dell e1405 WXGA+ wouldn't start"
date: 2006-11-03
forum: Hardware &amp; Laptops
---

### Post by DarkWulf on 2006-11-03
I had a pretty bad time installing edgy eft (clean install), so I just thought I'd share what I did to make things work.

I installed on a Dell e1405 laptop with the WXGA+ (truelife, whatever its called, gets you a 1440x900 LCD), and neither normal boot nor graphics safe mode would work. X would bail out saying that it was unable to find a display capable of supporting the needed display modes.

So, this is what I did (or at least, remember doing :))
[LIST=1]
[*]Ctrl-Alt-F1 to jump into text mode
[*]cd /etc/X11
[*]sudo nano xorg.conf
[*]Change things so they look like this: (bolded the things I remember changing... there may be stuff I missed, so please look and tell me if I missed anything...)
```
Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	**VideoRam	65536**
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
[B]	HorizSync 28-72
	VertRefresh 43-60
	Modeline "1440x900@60" 83.91 1280 1312 1624 1656 800 816 824 841[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
[B]	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "640x480"
	EndSubSection[/B]
EndSection

```
[*]After this I was able to at least boot into Gnome, in either 640 or 1024 resolution. (Thats why I have those modes listed...) (type startx on the commandline)
[*] I installed ubuntu to my hard drive at this point (so my changes would stick), and then rebooted from the HD. I'm not sure if that is required or not, but years of Windows have trained me to reboot so I don't lose data :))
[*] sudo apt-get install 915resolution (installs 915resolution to get Ubuntu to use the native res of your LCD)
[/LIST]

PS: If you want to go get compiz/aiglx/beryl/words you associate with 3dness, it is REALLY EASY with the integrated graphics that come with the laptop. In fact, it took me less time to get it working than it took me to get out of text mode. ](*,) 

Hope this saves someone some effort. (Tried to write it in a way that would make it easier to google for people with e1405s, but if you guys can think up a better way to explain what was wrong/how to fix it... I certainly wouldn't mind.)

---

### Post by leohart on 2006-11-08
I actually change the Default Depth to 24 and get it to work in a quite pleasing resolution.

---

### Post by DarkWulf on 2006-11-09
> **leohart said:**
> I actually change the Default Depth to 24 and get it to work in a quite pleasing resolution.

ummm... mine is 24 too?

I wasn't able to run native res immediately though w/o 915resolution

---

### Post by DarkWulf on 2006-11-23
I got a couple of questions via PM, so I'm going to stick it in here for others that wonder...

Umm, I tried to update my instructions to be a bit more explicit, but yah, please feel free to reply with more questions.

[QUOTE=ski309]Did you install from text mode somehow?  I did what your thread said before installing.  I wasn't able to figure out how to install after the directions you gave.

I realized after sending you the message that I should've just posted to the thread, so go right ahead![QUOTE=DarkWulf]Umm, to boot into gnome, I either shutdown the computer completely and then rebooted (type shutdown now), or hit ctrl-alt-backspace. (ctrl-alt-backspace works for me now, but thats with gnome already going. I honestly don't remember what I did.)

Something like that :)

I have XP Media Center on my laptop still. Seems to be fine...

PS, do you mind if I also post this in the forums so other people can derive some help from it? :)

[QUOTE=ski309]Hi, I read your thread about installing Edgy on your e1405, and I'm having the same problems.  I'm a little new to Linux so I'm not sure what to do after your instructions, about booting up to gnome.  How am I supposed to do that from the command line?  Also, the laptop has XP Home on it right now, will that cause a problem with your methods?[/QUOTE][/QUOTE][/QUOTE]

---

### Post by DarkWulf on 2006-11-23
(Sorry for the insane amounts of quotage, I just wanted it to be clear who was saying what)

[QUOTE=DarkWulf][QUOTE=kadymae]
Do you use wireless?  If so, has it worked, or did you have to tinker with that.  (I'm thinking to staying with the stock Dell Wireless 1390 b/g.)[/quote]

It works perfectly fine. Strangely, in some places at school I had difficulty connecting in windows (had to turn the wireless on and off and reconnect sometimes), whereas no problems with Ubuntu. No idea why, but it definitely does work :)

> Did you keep Windows? (I'm thinking of keeping mine for the sole purpose of running the program that would let my sync my eBookreader.)

yes, I still use windows.

PS: sometimes standby/hibernate doesn't work in Ubuntu. I usually just boot completely so it hasn't been too much of an issue for me, might be a deal breaker for you though.

Best of luck though, the e1405s get unusually good battery life[/QUOTE]

[QUOTE=DarkWulf][QUOTE=kadymae]Since Dell doesn't give you a disk (or, at least they don't anymore), how much of a problem was it to partition and not erase windows.[/QUOTE]

I backed up the rescue partitions that Dell had pre-installed (they're there so you can reinstall windows if need be), and then erased them in Ubuntu. If I remember correctly, by default my laptop came with four partitions, the first was a diagnostic partition, the second my full windows install, and then two "rescue" partitions (I can't remember the exact names right now.)

Mine was the 120GB HD, so I had a 105GB Windows partition. Thats the one you DON'T want to delete :) After that there are two smaller partitions that you can delete and turn into your root and linux swap partitions. (I think about 5GB or so.)

Install it into the area cleared up at the "end" of the disk (when installing I used the advanced partition GUI so I could pick where to install it to), which is the right-most of the display. Install proceeds normally, and things should work. I got an error about FAT something or other and should it check to make sure everything was okay, I just told it to ignore it. (The first time I had it check, and it didn't do anything at all, so I really have no idea why that happens xP)[/QUOTE]

---

