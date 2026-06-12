---
title: "My Shuttle X50 Chamsys MagicQ -project"
date: 2010-08-29
forum: Hardware
---

### Post by Tinamies on 2010-08-29
Hi!

I wanted to write here to gather the latest and greatest of  all the bits of information I've gathered so far to make my project  complete. Thanks in advance to everyone who are willing to hekp me.

My  projects goal is to build a platform for Chamsys MagicQ -light  controller software. For those who haven't heared about it, it's a  professional DMX-control software, ship in various forms. The software  it self is free and is used in also in the biggest light-consoles used  by stadium-sized bands. The big light consoles are shipped with linux OS  and touchscreen. What I'm using is MagicQ PC Wing which is a  USB-controller for the software and as DMX output for the light system.

To make long story short, here's what I need:

- light-weight solution PC w/touchscreen, no special requirements for CPU etc
- USB-support for Chamsys MagicQ and numpad
- WLAN-capability for VNC
- linux OS

As  for software, my goal would be to have two different bootup profiles.  One that would have ONLY MagicQ software and WLAN-networking with all  dependent services. And the second would have a "regular" set-up for  maintenance with browsers and such. So the actual "working profile"  would imitate the behavior in the bigger consoles. It would have MagicQ  software (demands X) as UI, and an agent daemon to start it up again if  it fails for some reason. (I've done something like this MANY years ago  on Red Hat, but I have no recollections how to do it now :D )

Here's the current status of the project:

[B]Shuttle X50 160GB HD, 1GB RAM w/ Ubuntu 10.04

[/B]- Display: [B]OK
[/B]- Ethernet: [B]OK
[/B]- WLAN: [COLOR=Red][B]NOT WORKING
[COLOR=Black]- [/COLOR][/B][COLOR=Black]Touchscreen: [B]works, but calibration is false on edges
[/B]- Chamsys MagicQ: **works, but with some strange functionality**
- Stripped boot-up profile: **NOT STARTED**
[/COLOR][/COLOR]
[U][B]WLAN:
[/B][/U]This  is what's puzzeling me most at the moment. Shuttle's specs only say:  "IEEE 802.11b/g/n", but according to Windows driver it should be RaLink  RT2860. However Ubuntu is loading RTL8191-driver. According to lsmod the  driver is not being used!

I would try to use ndiswrapper, but don't know where to get the .inf file.

[U][B]Touchscreen
[/B][/U]Touchscreen is working fairly ok, compared to the fact that I have NO idea why it is working! :D  Every time I boot the box, it seems to be using different drivers. As I  write this xinput list shows both EVTouch and eGalax, but I have no  idea which is in use. The only thing that really is a problem is the  calibration which seems to be a bit different every time I boot, but  every time it's really unfocused on the edges. This is very vital for  MagicQ usability.

[U][B]Boot profiles
[/B][/U]Should you have any ideas where to start, 'll be pleased to know!

---

### Post by Frankiewizard on 2012-06-11
I have started using Chamsys it really does not seem to work on ubuntu 12.04 with a (64) bit machine & thats a shame because I have been using w****** to do lighting for years & it stinks. I would prefere to use a LinuX system but to no avail. 

Compaq Presario CQ 62

---

