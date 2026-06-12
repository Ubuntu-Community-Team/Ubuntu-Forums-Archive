---
title: "what's a good netbook with next to no problems?"
date: 2010-10-01
forum: Hardware
---

### Post by kraylus on 2010-10-01
greetings from iraq!

im currently deployed over here for the next year and i've recently setup a website for my platoon to upload pictures and videos for their families and friends without having to worry about facebook/myspace policies, image resizing, limits on video length, etc. etc.

my normal laptop i use is too large and bulky to be taking out on missions and i paid way too much money for it on top of that. last thing i want is for my gunner to drop his 240 on my pack and crush it.

im needing a netbook that's not ridiculously expensive (alienware's mx11), has awesome battery life, dual-core proc, usb 3.0, wireless N and a built-in webcam.

the tricky part is... i want all that hardware to work flawlessly in ubuntu. ive been reading about people who can't get their headphone jack to work, can't get the kernel to do smp for their dual-core, etc. etc.

i intend to  use the netbook for web development, paperwork, music and the occasional movie before i rack out.

ive got my eye on the [asus eee 1015pem]("http://liliputing.com/tag/asus-eee-pc-1015pem").

any thoughts?

---

### Post by ajgreeny on 2010-10-01
Not a true answer, but have you seen this?  It might help you make a decision.
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by kraylus on 2010-10-01
the netbook im lookin at is unfortunately not in that list. but it seems alot of the newer asus netbooks are in tier 1. so at least there's that. i dont imagine ill be having too many problems with it.

does anyone know anything about them system 76 machines? they perform well?

half  the fun of linux is installing and configuring, but at the same time, if it can work great out of the box, even better.

---

### Post by Scooter_X on 2010-10-14
System76 systems are supposed to work perfectly out of the box. But maybe that's why they're a bit more expensive. I am shopping around right now for a netbook, and my first thought was System76. But as I've been shopping around, I'm realizing they're expensive, but lack the bells and whistles of other netbooks at the same price. Granted, if this Asus Eee 1015PEM doesn't work absolutely flawlessly with Ubuntu, you've probably got a netbook that performs as well as the system76 starling. *plus*, the starling only has half the battery life. 

Seems to me you could spend $100 less and get just as much computer if you avoid the starling and go with one of the Asus Eee systems. But then, I'm just shopping around and forming opinions as I go. Maybe someone else has better insight? But I would like to know how well the 1015PEM works. If so, I'm definitely getting one.

---

### Post by paulscode on 2010-11-06
I bought the 1015PEM and tried both Ubuntu 10.04 and 10.10 on it (64 bit versions of both, since the Atom N550 is a 64 bit dual core).  So far, everything on it seems to work well except the internal wireless card (which is kind of important).

In Ubuntu 10.04, none of my wireless networks show up (I have two of them, an n and a g).  In 10.10, the networks show up and I can type in the WEP key, but the computer never actually connects successfully (it always times out).

I believe what I need is to get the proprietary Broadcom STA Wireless driver installed, but not having any luck using the two or three suggestions that come up in google (not sure if it is a 64 bit issue or just "user error").  I'll post  here if I get it working, in case anyone else is thinking of getting this netbook and plans to use Ubuntu on it.

---

### Post by paulscode on 2010-11-07
Everything is working now.  Turns out my particular 1015PEM has a Ralink RT3090 wireless card, not a Broadcom as most others seem to.  This is easy to figure out by running the command "lspci" from the terminal and look for the "wireless ethernet" entry.  I found a repository that has 64 bit drivers for the RT3090.  It doesn't currently support Ubuntu 10.10, but it works fine for 10.04.  Ralink's website has the source code for the driver, so theoretically one could compile it themselves for Maverick rather than acquiring it through Synaptic, but I'm happy to use Lucid for a while until Maverick is supported by the repository.

For anyone interested, the repository for the Ralink RT3090 is:
**ppa:markus-tisoft/rt3090**

This can be added via:
**System->Administration->Synaptic->Settings->Repositories->Other->Add**

Then Reload Synaptic, search for** rt3090**, mark for installation, apply, and reboot.  Voila, the wireless card works!

---

