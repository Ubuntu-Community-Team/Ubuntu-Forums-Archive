---
title: "Radeon mobility rendering problem"
date: 2009-10-30
forum: Hardware
---

### Post by Mr Roboto on 2009-10-30
I have been searching high and low for a solution to this problem but I can't find anything that gives me a good idea of where to start with it.

I have upgraded to Karmic on my laptop, and there is something wrong with the rendering of certain application windows. So far I have noticed it with the System Monitor, and with the pop-up notification windows.
I have attached a screenshot of the System Monitor to show what I mean.

My video card is reported by lspci as:
VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

Any suggestions would be greatly appreciated.  Before upgrading all of the rendering was fine and working properly.

---

### Post by colinpat on 2009-10-31
I have IBM A30 with Radeon Mobility M6 LY chip and have display problems as well.  Desktop dispays ok but when you open an application you only see an outline of the window.  All worked ok before upgrading to 9.10 last night

---

### Post by sampster on 2009-11-03
Same problem here with T42 and Radeon Mobility 7500. After upgrade to 9.10 display gets corrupted with some apps.
I did some testing and it seems that system manager, volume and brightness OSDs get distorted with metacity but with compiz they work fine.
However, also compiz crashes occasionally, so I guess the problem is somewhere else.

---

### Post by DOXI on 2009-11-18
Same problem here. I'm using a IBM X31 with a Radeon Mobility M6 LY graphic card.

No updates on this problem? :(

---

### Post by james_xxx on 2009-11-23
I am also experiencing problems on an old Medion Md5275 laptop (purchased in 2003 from Aldi's, of all places). It has the Radeon Mobility M6 LY GPU, as well.

The screen burned out on this machine a few years ago, but I still use it as a spare off and on, with an external monitor. 

My experiences so far...

Machine worked well under Ubuntu 9.04, which is what it is now running again.

It locks up upon trying to boot from the Ubuntu 9.10 install CD. When it gets to the point of trying to load the desktop, I get a white screen and a mouse pointer. The pointer will not move, however.

Interestingly, I was able to boot from a Mythbuntu 9.10 CD, although it went haywire upon trying to enable Xfce4's compositing manager.

I then gave Fedora 12 a shot. It installed just fine, but when trying to use the Gnome display settings, I was given no option for a screen resolution higher than 800x600. I could have spent some time creating xorg.conf, and playing with hundreds of possible configurations that may or may not have worked, but I didn't.

So, for now, it is back to Jaunty. 

I would love to hear if and how others have been able to get this GPU working well under Karmic.

Thanks!

---

### Post by f0ku5 on 2010-01-10
I am also experiencing this problem with Ubuntu 9.10 on an IBM ThinkPad X31

---

### Post by ben1986 on 2010-04-09
Hi Guys,


No luck on this front?  I just dual-booted Windows 7 and Karmic Netbook Remix on my X31 thinkpad, and I'm having an absolute mare with the desktop effects, there is a crazy purpley-green static effect obscuring all the icons, making the text unreadable.  As soon as I open an application, the application runs absolutely fine, no problems at all.  I think its all the swish transparency effects in the new menu, does anyone know how to turn these off?

My graphics card is ATI Technologies Inc Radeon Mobility M6 LY

---

### Post by executorvs on 2010-06-11
I'm gonna pull my toshiba satellite out of the closet and see how things are going in lucid and maybe I'll step back to Karmic later.

as I recall compiz didn't work out of the box in jaunty but I think metacity compositing did. has anyone tried that in Karmic?

---

### Post by stiiixy on 2010-10-04
If anyone can find the time the M6 became problematic and then pair that  to the driver update that rendered it useless? Maybe just try an install, then do an update to see if they work differantly for starters.

I am also running a X31 and have not had proper 3D acceleration or easily configurable acceleration since around the 9.04 mark. And alas, I cant test it now because I am in Europe without my beloved portable CD-ROM!

---

