---
title: "Display problems/weirdness"
date: 2008-08-17
forum: General Help
---

### Post by crackseller on 2008-08-17
Hi guys,

I have a small desktop pc (aka "Nettop") which basically consists of laptop parts. Now the problem is, for some reason, Ubuntu detects 2 displays attached to the pc, which is wrong. There's only one display attached. However, Ubuntu thinks there are 2 but since there's just 1 (physically) it basically puts the first display above the 2nd. See how that looks:

[[IMG]http://img176.imageshack.us/img176/3346/screenshot1eq7.th.png[/IMG]](http://img176.imageshack.us/my.php?image=screenshot1eq7.png)

That's just one of the problems that come with this weird behavior of Ubuntu. Another would be sometimes weird stuff happening during video playback etc. The worst part is, that very often GDM/Gnome would be not visible after I start Ubuntu because Ubuntu is trying to display the window manager on the wrong (non-existing) screen. A reboot helps most of the times.

I need to get rid of that other non-existing display. How do I do that? I already tried displayconfig-gtk. There I just set one display to disabled but it still is detecting 2 displays. So does the tool "System > Preferences > Screen Resolution".

dpkg-reconfigure xserver-xorg doesn't let me set anything up but the keyboard. There are no options to select my graphics card etc. displayconfig-gtk however tells me that it is using the i810 driver which is correct for my Intel GMA 950 graphics card. In a sense the graphics card works correctly in terms of resolution and refresh rate. Even compiz/beryl works fine. It's just that I have this display problem.

Btw. my xorg.conf is looking strangely generic:

```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```
No matter what I do (displayconfig-gtk or dpkg-reconf xorg), it doesn't apply any changes to the xorg.conf, which is also strange.

Well, I'm out of ideas and I desperately need help. I cannot bear with this crap any longer. Any ideas are welcome.

Thanks!

---

### Post by crackseller on 2008-08-18
Nobody an idea whatsoever?

---

### Post by crackseller on 2008-08-19
Oh come on guys, someone must know a solution. Let me raise the stakes: I am hereby threatening to switch back to Windows XP!

---

### Post by mb_webguy on 2008-08-19
> **crackseller said:**
> Oh come on guys, someone must know a solution. Let me raise the stakes: I am hereby threatening to switch back to Windows XP!

Hey, that's extortion! :wink:

That's certainly an interesting problem, especially considering your xorg.conf file (which is indeed impressively generic).  What happens when you go to System->Preferences->Screen Resolution and click "Detect Displays"?

---

### Post by JohnLau on 2008-08-19
Maybe you can try using the 'intel' driver instead of 'i810'

Or you can try booting recovery mode and select xfix

---

### Post by crackseller on 2008-08-19
> **mb_webguy said:**
> That's certainly an interesting problem, especially considering your xorg.conf file (which is indeed impressively generic).
As I found out, the xorg.conf in Hardy does look like that. Apparently they changed something which makes it obsolete to use xorg.conf for the X Server setup. You may still use xorg.conf, though. I did try a couple of things using xorg.conf but always ended up where I am now.

> **mb_webguy said:**
> 
What happens when you go to System->Preferences->Screen Resolution and click "Detect Displays"?
It will detect 2 displays, my Samsung widescreen LCD (which is correct) and another 1024x768 generic display.

@JohnLau: Recovery Mode doesn't make any sense, as there's nothing to recover from. Ubuntu detected the 2 displays ever since I installed it 5 days ago. Also, it is working fine, with the exception of this totally weird display problem. Changing the driver doesn't help either.

Thanks for the input so far. Keep it coming! :-)

---

### Post by crackseller on 2008-08-21
I switched to Arch and to my surprise it works like a charm. No issues with the xserver let alone gnome, or anything like the problems I encountered as described here in this thread. I'm really happy about it but also sad that Ubuntu didn't do it for me anymore, after all that time. I'll give 8.10 another try, I guess. Until then, farewell!

---

