---
title: "Acer 8935g, problem with ATI 4670 (second GPU)"
date: 2010-02-10
forum: Hardware
---

### Post by unknownofflineuser on 2010-02-10
Hi,

I have Acer 8935g with two graphic cards:
- low power Intel series 4
- ATI 4670 (HDMI and DIsplayPort are connected only to this one)
Ubuntu x64 9.10, 2.6.31-19 kernel

The problem is I can't get ATI working - by default Ubuntu uses Intel (that's OK, but I need HDMI) 
It would be fine to just disable Intel somehow and continue with ATI (no BIOS switch :()
When I install ATI driver from System->Hardware Drivers or from ATI site, X just doesn't start - non-blinking cursor in left upper corner, other consoles are screwed too.
Another strange thing - before installing drivers I tried to just Xorg -config with no any success.

Possibly someone solved this issue or can give some directions at least (I am new to xorg.conf & etc)



UPDATE:
with dualhead I got picture upon external monitor only.
checking logs gives nothing - seems fglrx just works with no correct display attached.
how could I get a list of monitors-options to use in xorg.conf? aticonfig --query-monitor says no X running and no $DISPLAY set - what I should set to?

---

### Post by Prometheus_IX on 2010-09-07
Hi unknownofflineuser,

Unfortunately I don't have any advice particularly, HOWEVER, I also have an 8935G and have had problems with the ATI card, specifically, i installed the proprietary drive from AMD and it stopped any graphical version of Ubuntu being able to startup.

I tried to revert through a terminal loggin but no luck, so I ended up backing up my data through that and reinstalling Ubuntu - not ideal!

I have a feeling this laptop is not particularly suited to Linux - on the Ubuntu 9 release the original kernel doesn't support networking (wired or wireless) so I had to update the kernel manually, and I'm having massive heat issues which don't happen at all in W7...

Alex

---

### Post by unknownofflineuser on 2010-09-08
The problem is in two graphic cards - in windows when you switch between them, some additional driver switches screen panel to active one. In Linux such a driver is missing (actually Acer could provide it I suppose with much effort).
That's why when install radeon driver and activate it you've got blank screen - screen is not connected to video card - it is always connected to embedded intel video. Upon external HDMI monitor I got picture this way. I plan to make dual video card X setup to use radeon with external monitor.

All other hardware works for me fine in 9.10 and 10.04, possibly propritary wifi driver needed activation.

---

### Post by gingaman on 2010-09-23
Hi Guys,

Dunno if this will help?

I've own the same laptop and I'm trying to get the GPU switch to work (I currently dual boot Win 7 and Fedora).

Have you tried switching on your laptop using the button opposite the 'hold' button on the media control pad? This should boot your laptop with the ATI card.

Unfortunately for what ever reason, video playback is very dark (the desktop is ok) in all the media players I've tried , I'm guessing a driver issue.

I've also had very results using Catalyst from ATI, although I may try again to see if I can resolve the issues.

Steve

---

### Post by unknownofflineuser on 2010-09-23
Hi Steve,

Thanks for this info!
Will try it asap.

---

### Post by Unfrog on 2010-10-23
Hello, I have the same laptop. After the previous Ubuntu died (cat jumping on the power button during update... really! :D ) I installed Ubuntu Netbook 10.10 with the windows installer. I decided to try the ATI card again. After installing the drivers, GUI doesn't load, but I get the basic console to log in.

I tried gnome-session from there, but get an error 'cannot open display' (1551) with no other details.

Trying Steve's advice gets me to the desktop view, but opening any application window laaags the system to the point where the mouse pointer is hard to use and the gradient on top of the window is displayed wrongly (pixels of a different color here and there) Changing to a single-color theme doesn't change it, apart from the display mistakes.

After uninstalling the drivers booting normaly works. Booting with the other button gives a darker display at first, but then gives the same results.

I'm not experienced with administrating/configuring Linux, but could give it a go, if you tell me what to try.


PS: Did any of you experience random system freezes? Happened on the previously installed Ubuntu and twice on this one. Also the ubuntu one and some other programs would just do nothing when run. no reaction at all.

---

### Post by unknownofflineuser on 2010-12-12
Hi all,

So Acer solved our problem (partially) - latest BIOS update enables video card switch in BIOS setup.
ATI works for me in 10.10 without any effort.


Andrei

---

