---
title: "ideas to how to use a old busted up laptop."
date: 2020-01-09
forum: Hardware
---

### Post by wolftrax on 2020-01-09
I read a couple of threads and articles on how to use a old laptop for servers or build them into televison sets and all sorts of creative ways to use a old laptop for something else instead of just getting rid of it.  I cant find it on google but one guy posted a picture of how he just build into a homemade cabinet making it look like those old arcade games and a other had made it into a televison set by using a old colour television set that he managed to build the laptop into and using the screen from the laptop and usb ports for plugging in usb keyboard and mouse. 

one had simply just taken the motherboard and disc drive and made into a headleass server and did not even bother to build a case for it , just to play around with it. 

suggestions on how to reuse a laptop is usually something like servers or hardware firewalls but I don't really have anything to use that for but I own a old laptop that the keyboard is broken on ,  the power button is loose and the DVD drive is trashed so I cant really use it for much because there is only two USB ports on it so even if it still works I don't have any extra usb ports for exeternal storage devises or external burner and I just used it for beta testing up until now. 

i had this laptop for 13 years and I am not willing to let it go yet but I cant fix the keyboard on it.  I spilled beer into it and broke of two keys being drunk and surfing the internet  :) 

any ideas on what I can do with it  ?  I don't mind taking it apart and experimenting with it because its not usable for anything as it is really.   but motherboard and screen works and apart from the power button is likely to break off one of these days it still works.

---

### Post by QIII on 2020-01-09
I once used one to make a large-format electronic picture frame.  I could even run video loops.  I have one based on an R Pi right now and that works like a champ.

I've seen things like mirrors that use two-way glass with a monitor behind to display the weather and such.

Use a usb keyboard to install Ubuntu, then ssh into the machine to interact with it.  My current R Pi picture frame I just SSH into over wifi to change the loop or image displayed.  The power is run through the wall, so no unsightly cables.

[ATTACH=CONFIG]284773[/ATTACH]

---

### Post by wolftrax on 2020-01-09
cool.  actually one of the first ideas I had apart from making a arcade gaming console , but to make that I need to figure out how to get joystick on it and it will be too large a project to start with.  

a picture frame is a good idea but I was thinking about building it into a suitcase and use it as a large portable PDF reader just for the fun of it ;) 

or off course build a case and make a headless server or hardware firewall but I don't really need something like that.

---

### Post by Frogs Hair on 2020-01-09
Arduino is great way to get into projects, but requires a kit to get started.The software is free/opensource.

---

### Post by crip720 on 2020-01-09
Liquid and laptop keyboards usually do not mix well together. Got lucky only keyboard stopped working.  Can use USB hubs if more ports are wanted.

---

### Post by wolftrax on 2020-01-11
I would consider getting such kit someday. it sounds interesting.  however I own several computers I just tinker with , usually laptops .

---

### Post by TheFu on 2020-01-11
There is a point where old is just old.  13 yrs old means 2007-ish laptop.  That is before integrated graphics (or any) had hardware support for mpeg2 or h.264 decoding, so any video will be limited to about 600p - or whatever the CPU can keep up with.  A legacy video game system would be about the only video use I can see.

2 USB ports isn't a limitation. Get a powered external USB hub and you can add 7+ other devices. Just keep the keyboard and mouse directly connected to the machine. There are $4 "Y" cables to share a single USB port with older ps2 mice+keyboards.

If you tinker, getting a KVM-switch would be a good investment. 4-16 computers connected to 1 keyboard, 1 video, and 1 mouse.  Newer ones have audio and USB port switching too.  The hardest part is the video, since the last 2 generations have dropped VGA, so you'll want HDMI and will need that or an adaptor for each computer.

When I'm trying to decide if an old computer is just an old computer that needs to go ... I look at a $35 Raspberry pi.  If the r-pi can do it, whatever "it" is, better, cheaper, and well-enough, then I know it is time to give the computer away.

If you don't have a backup server, that would be a useful thing. Everyone needs a backup server that can "pull", versioned, backups from their other systems.  Almost any x86 would be better at that than any raspberry pi because most Pis have limited I/O capacity.

---

