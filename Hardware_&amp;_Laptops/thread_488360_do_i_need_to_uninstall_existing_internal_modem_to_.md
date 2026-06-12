---
title: "do i need to uninstall existing internal modem to recognise external modem"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by vargind on 2007-06-30
So, what happened is I downloaded the linuxant drivers for my conexant internal modem, but then I stopped the package install halfway (because I decided I wanted to try the open source drivers). and then I possibly maybe got connected to the internet using the open source conexant drivers, but I'm not 100% sure, because the first thing I tried to do was look at all the packages I could download, but it wouldn't let me until I completed the linuxant driver install, and then the connection speed of course was stuck at 14kbps so who knows...

anyway, I've got this old external modem with serial-port connection, but I'm not quite sure how to get the computer to recognise it. it only seems to want to recognise the internal modem as far as I can tell. I'd like to use the external modem instead of being stuck at 14kbps... but I'm a real newbie, what do I do?

---

### Post by theDaveTheRave on 2007-06-30
Vargind.


Your question is kinda ineresting.

could you clafiry a few things.

is your external modem an old fashioned 56kbps analogue or is it a highspeed bradband type?

if it is analogue you could probably get away with using wvdial, I used to use this solution when my  first Linux experience was with SuSe 9.0 - worked well but was slow, but then at that time broadband was only just coming into being.

Working from memory the setup page would allow you to set the device that was being used (tty0 or similar as it is an external). I suspect that wvdial is now set up to work with broadband routers also, so check out the forums for wvdial.

Removing the Old linuxant drivers should be relatively easy using apt or the installed package manager - you may however have to complete the install first then remove it - to ensure that all the changes are updated.

run the <lshw> (list hardware) command from a terminal and then plug in your external modem and do the same again, and see if there is any difference, if it is recognised I assume it should show up in the output.

I'm sorry if I haven't been much help, I'm only a relative newby myself, and I'm still learning all the various Linux command line stuff from the forums.

good luck and remember to post and results bakc here as I would be interested if this had the desired effect.

Dave

---

### Post by vargind on 2007-07-02
hi, thanks for your reply.

it's a 56k modem. I've been searching around today and it seems like it should be possible to get it working under linux.

it doesn't seem to show up when I use <lshw>

(as an aside, winxp doesn't like it either. it thinks it's an AC97 audio device)

i'm wondering if the internal modem having assigned itself as /dev/modem is causing problems, and whether I will need to remove the internal modem to get it working...

---

### Post by theDaveTheRave on 2007-07-02
Vargind

is it a USB or paralel port connection?

check out the following for setup details.

[www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)


it states that you may need to ensure that you have the drivers installed.
 
if the device isnt' recognised in XP that is probably because of the drivers issue.

It should however appear in the list of devices in the wvdial setup screen, you'll have to check the "port" that it is connected too though, or maybee simply cycle through them untill it works.

Unlike USB it may not respond when you do a system scan - as this sort of paralel port doesn't support plug and play (I expect, but don't quote me on it)

If it is USB try listing the usb devices <lsusb> and it will give details of the chip setup etc 

here is my output

[quote=]
davemyers@Aramis:~$ lsusb
Bus 005 Device 002: ID 0402:5602 ALi Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:c401 Logitech, Inc. TrackMan Marble Wheel
Bus 001 Device 001: ID 0000:0000  
[/quote]

the ID details of <046d:c40> are the chip setup details of the device (in this case my external wheel mouse), plug this into the search on Ubuntu and see what it throws up, or alternatively head for the sourceforge site.

good luck

Dave

---

### Post by vargind on 2007-07-02
the modem is connected by serial port, it's on ttyS0

when I run wvdialconf the lights on the modem briefly flicker as the program talks to the modem, but the output of the program says something along the lines "trying at 9600, trying at 50000, trying at 115000 - no response, giving up"

pppconfig can also be directly set to use ttyS0, but it won't get the correct lights to light up on the modem at all

I think I'm going to have to give up

---

### Post by theDaveTheRave on 2007-07-02
Vargind.

sorry feeling like I can't really help any further.

I guess that I could try getting out my old 56Kbs modem and have a play on the old machine, and plug it into the phone to see how the setup works (or not). I don't know when I will get time to play, as I may have hidden the unit in the loft somewhere!

I assume you are using Feisty?

You mentioned that the device doesn't work with XP.

It obviously worked with something? or is it a new device? in which case take it back to the shop and see if they can get it to work on one of thier pc's - or if you have an old one hanging around.

Have you searched for the drivers for the device? It may  be you need to wrap it up in some way. Have you checked the sourceforge compatibility list?

Being external it should be pcmcia compatible straight out of the box.

The thing that bothers me is that the unit doesn't seem to be being recognised at any speed from wvdial.

The next option is a know good unit.... which is why I will try to find mine and have a play to see about the setup.

keep posting to give me a kick or I may forget!

Dave

---

### Post by Bartender on 2007-07-02
Tell us more about this modem.  What brand?  Model?  I've got a funky old Boca serial external modem that isn't recognized in KPPP.  Plug in my old USR Sportster and KPPP sees the modem, talks to it, gives me back a string of AT commands...
More input
Feisty is really stupid about dial-up.  Worse than Dapper!  You might want to try MEPIS or PCLOS or even Puppy Linux.  I keep hearing Puppy works better with dial-up modems than Ubuntu.

---

