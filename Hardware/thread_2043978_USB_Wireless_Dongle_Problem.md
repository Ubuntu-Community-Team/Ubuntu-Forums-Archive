---
title: "USB Wireless Dongle Problem"
date: 2012-08-17
forum: Hardware
---

### Post by zombygeek on 2012-08-17
Today I decided to go back and duel boot my PC with Ubuntu again. I got a new PC not to long ago and was happy with Win7, but now I feel like messing with Ubuntu again.

In Windows I use a Quest USB wireless Dongle to get online. But in Ubuntu it doesn't work.

My idea, since I have an Ubuntu laptop with a working wireless connection, was to use ICS to the desktop, so it could install the proper drivers for the dongle. The problem with that, is, I think it needs to install the drivers for my lan networking things as well, because I can't get ICS to work.

If I can't get the dongle to work, I'd at least would like to have a working ICS from the laptop to get online with.

Any ideas for getting my online?

---

### Post by ahallubuntu on 2012-08-17
You could use ICS this way:  put your desktop (Windows) online with the Qwest dongle.  Then bridge that internet connection to either the wired LAN card or another wireless card you have installed on the desktop.  Then you could connect the laptop to it with an ethernet cable or an ad hoc connection.

Alternately, if the desktop isn't that slow, just install Ubuntu in a virtual machine in Windows on it and mess with it that way.  Windows would still be running and connected via Qwest.  The virtual  machine guest (Ubuntu) would get its network connection from the host (Windows).

Try [www.virtualbox.com](www.virtualbox.com) for free virtual machine software from Oracle.

---

### Post by zombygeek on 2012-08-17
Well, my desktop isn't slow at all... 6 cores at 3.33 ghz is pretty good I'd think.. I already have virtual box installed and I've used it before.

I still want to get this working though, I like using gnome3 a lot and it seems impractical to load up virtual box each time.


I'm not exactly sure what you mean with setting up the ICS.

My set up is:

Desktop (ubuntu/win7, usb dongle) ---------- Laptop (ubuntu, working wireless)

Your saying I should create the ICS with windows and laptop, then flop the desktop over to ubuntu and it'd still work?

EDIT: I also forgot to mention that my lan networking is in the mother board, and isn't a separate card.

EDIT: Solved one problem.. Apparently my lan was disabled on my desktop in windows. turned that on. not sure if it'd change anything in ubuntu though...

---

### Post by ahallubuntu on 2012-08-17
I was offering you separate suggestions.

One suggestion was to use Virtualbox and install Ubuntu on the desktop there.  Then you would avoid all of the awkwardness of trying to use ICS.  But it sounds like you've already done that and want to do something else.

The other approach is ICS.  In this, you bridge together two network connections on a computer so you can share the network.  On your desktop, you have a wired connection and this Qwest Dongle that puts you on the internet(?).  I'm suggesting you bridge these two connections together with ICS.  Then, connect your laptop (with Ubuntu native, not virtualbox) to your desktop to share the connection.

It might be a lot easier to use ICS to wire the desktop to a wireless router, using the single ethernet on your desktop.  Then you can just connect the laptop to a router wirelessly, the way it connects normally to hotspots, without any of the complications of ICS setup on the laptop.    I don't know about you, but I can find cheap wireless routers - sometimes new ones for $20 USD or used ones, even G routers for $10 or so.

ICS to me is still an awkward way to connect to the internet.  It should work, but it may not be that fast or reliable.  Try it and see how it works.

---

### Post by zombygeek on 2012-08-19
I've used Ubuntu for a long time, just not exclusively, and now that's what I want to do is all.

Part of the problem is that my modem and wireless router are downstairs and I can't move them from there because I have satellite internet and that's where the guy drilled the satellite cable through the wall at, so I'm wireless only.

I've used ICS on Windows before I had a dongle and it always worked fine for me. I may just give in though and buy a cheap N USB wireless adapter that's guaranteed to work. I feel like the one I have now may not be the best anyway, and it's large and sometimes hogs another USB port. Thanks for the help anyway.

---

### Post by kurt18947 on 2012-08-19
When I saw Quest I was thinking cellular data then I see satellite internet.  If your  dongle is a conventional WiFi adapter it might be worthwhile to run "lsusb" and see if it comes up with something like this:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]**
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

You could then post the output here and also google your equivalent of 

** ID 0846:9030 **+Linux.  

The 2 groups of 4 characters identify the manufacturer and model I.D.  It might be a chipset from Ralink or Broadcom or RealTek or somebody like that.  It may be possible to get your existing dongle to work.

---

### Post by zombygeek on 2012-08-25
Sorry for the late response. I've been busy lately.

The problem with lsusb is that it doesn't show up at all. From googling it I learned that other people with the same adapter and the people with the action tech version of the same adapter, have the same problem.

It's because it has a small flash drive inside which has the windows drivers on it. For some reason that makes it not work in Ubuntu at all. I couldn't find anyone who ever actually got it working :/...

---

### Post by kurt18947 on 2012-08-26
> **zombygeek said:**
> Sorry for the late response. I've been busy lately.

The problem with lsusb is that it doesn't show up at all. From googling it I learned that other people with the same adapter and the people with the action tech version of the same adapter, have the same problem.

It's because it has a small flash drive inside which has the windows drivers on it. For some reason that makes it not work in Ubuntu at all. I couldn't find anyone who ever actually got it working :/...

If the adapter doesn't show up in 'lsusb' I think I'd be looking at plan 'B'.  Sounds like the O.S. doesn't even know the device is present, let alone how to work with it.

---

