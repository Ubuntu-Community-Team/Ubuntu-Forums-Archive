---
title: "Karmic on Thinkpad T42"
date: 2010-01-23
forum: Hardware
---

### Post by keithpeter on 2010-01-23
Hello All

"Refurbished slimline notebook powered by an Intel Pentium M 1.7 Ghz processor, includes 1024MB RAM, 40GB hard drive, CDRW/DVD Combo drive, wireless network" with "ATI Mobility Radeon 7500 graphics - AGPx4 32MB DDR SDRAM, 1024 by 768 screen"

Any known show stopper issues with Karmic? I'll need hibernate to disc working, wifi and will have to dual boot :-(

I've googled

Cheers

---

### Post by keithpeter on 2010-01-31
Hello

It turned out to have 64Mb video and a 1400 by 1050 pixel screen. The reason I could not find much past Ubuntu 8.04 on this box is that most things seem to work fine: video detected, wifi work.

There is a known bug on hibernate (error message on hibernate, then can't resume until you restart by holding power switch down). That is annoying but survivable.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350680](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350680)

May be resolved  by installing a different hibernate manager

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332827](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332827)

---

### Post by McNuggets on 2010-01-31
I have found that there is a few graphics issues with 9.10. It's usually the window borders and such that display incorrectly. And yes the hibernate issue is a real pain in the rear.
 
I would suggest 9.04 but nothing newer, because I have had great luck on my three t42's over the last few months.

---

### Post by anthony_barker on 2010-01-31
I have been running it since it came out on my t42.

Aside from video driver issues Ive had not problems.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/429295](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/429295)

Actually had video issues on 9.04 as well.Mostly livable by changing my Xorg config..

---

### Post by Kantis on 2010-02-01
I have a very similar T42 too. Karmic fixed the load cycle bug it had had since Hardy. The most annoying issue now is that the network notification "speech bubble" is a garbled black mess and I haven't found a way to fix it or turn it off. Otherwise no worries.

---

### Post by keithpeter on 2010-02-01
Hello chaps

I seem to be lucky so far (touch wood). Its a T42 type 2373-563 if that helps

@McNuggets: I'm not seeing any particular strangeness with window borders at present. Firefox is rendering some web pages oddly (the Iron version of Chrome is fine). I have effects switched off as I don't want to waste processor cycles on window physics, I'll buy an iPad for that, this machine is for getting a job done :p 

@anthony_barker: I've not seen any big video issues at present. This is a clean install from a 9.10 CD-ROM, resized the windows partition and everything.

@Kantis: Is that the black thingy that opens on the upper right hand side of the screen when this laptop picks up my wifi? Is readable (but I preferred the yellow tool tip popup in the status bar some versions ago).

Irony: when I upgraded the windows partition to XP service pack 3, the wifi stopped working. Workaround is to fall back to earlier drivers, walk three times anti-clockwise round a church and crush and eat garlic :evil:

In summary:Not bad for a little over a £ton with delivery and 2.5 hours battery life with the battery supplied.

Cheers

---

### Post by Botham on 2010-11-13
Thinkpad T42P in docking station with 1400 x lenovo lcd monitor - all perfectly configured out of the box with my first install of Ubuntu Studio 10.10 (Maverick) this evening.

The native resolution for the monitor connected to the docking station looks perfect so not looking into this but thought I would post as I took the punt successully with current version.

WiFi not working yet that's next

---

