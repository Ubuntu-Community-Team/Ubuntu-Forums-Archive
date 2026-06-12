---
title: "How to work with switchable graphics of t400"
date: 2009-02-02
forum: Hardware
---

### Post by eeshan on 2009-02-02
Hi,

I just got my lenovo t400, on which I wish to configure the graphics adapters. I have got my system working on either Discrete or Integrated graphics only [not switchable].
The problem I am facing is that I get the same battery backup on my 6-cell battery. (approx 3 hours 10 min for both integrated and discrete).
On the other hand, I get 4.5-5 hours on integrated and 3 hours on discrete in Vista.

I wish to run my system on the integrated graphics mode and get a healthy battery life (3 hours is a bit low for my requirements). Can anyone please post a howto for getting proper battery backup using integrated only mode.

My xorg.conf looks like this:
> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by in-dust-rial on 2010-05-01
hi,
i guess you were already using the BIOS setup to switch?
( I noticed, that the settings are resetted - i guess by windows )

however, i can see a difference in powerconsumption ( a quite big one).


quote thinkwiki:
```
  Development status:

David Arlie has been working on switching between GPUs without having to reboot, and changing BIOS settings. An initial version of a new driver (vga_switcheroo) has been merged in the 2.6.34 kernel. This driver allows switching between graphics cards, but requires that the Xserver is restarted. Full seamless runtime switching support will require significant Xserver work. 

```

thinkwiki:
[http://www.thinkwiki.org/wiki/Switchable_Graphics](http://www.thinkwiki.org/wiki/Switchable_Graphics)

please report your findings!
since your post is almost a year old, it might give crucial insights?
hf

---

