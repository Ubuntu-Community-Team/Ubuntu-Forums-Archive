---
title: "Wireless Cards and Ubuntu"
date: 2004-11-04
forum: Hardware &amp; Laptops
---

### Post by DoubleDangerClub on 2004-11-04
Any recommendations of wi-fi cards that play nice with Ubuntu and have scanning capability?

DDC

---

### Post by mercurus on 2004-11-04
[QUOTE=DoubleDangerClub]Any recommendations of wi-fi cards that play nice with Ubuntu and have scanning capability?

DDC[/QUOTE]
 I haven't tested it as yet, but I have a NetGear WG511 (a PC-Card 802.11g adapter) in my laptop. I use it under Debian with a 2.4.26-patched-to-death kernel, but as of 2.6.5-rcX the prism54 ([http://www.prism54.org](http://www.prism54.org)) driver is included in the stock kernel. In short, I would imagine that Ubuntu will detect and load the appropriate kernel modules (drivers) to make a prism54-chipset based card such as the NetGear WG511 and WG311 easy options. You may have to download a firmware for the card, but it is available at [http://www.prism54.org](http://www.prism54.org) and is very simple to install, just create a directory and rename a file. I'll be testing this as soon as my exams permit :x and I'll write a document outlining my experiences.

As far as "scanning" goes ... the prism54 chipset is supported by Kismet (after version 0.8), arguably the best AP detection software available for the i386 Linux platform. All the usual suspects (except airsnort at last check) will function nicely with this card. That said, there is no scope for an external antennae, and others with more experience can probably suggest an appropriate card. As a cheap or budget 802.11g chipset \ card:

NetGear WG511 (using the Prism54 chipset) gets my vote of approval.

Cheers
mercurus

---

### Post by randy on 2004-11-04
I'm running an Atheros based wireless card.  The driver is a little strange.  It's a closed source hal with an open source driver but it comes in the restricted packages for Ubuntu.  It does a pretty good job of scanning using Kismet.  I've used it once before.  It's got 802.11B and 802.11G support.

---

### Post by Jspired on 2004-11-04
The Netgear WPC-11 (V 3) was plug and play for me; worked out of the box.

The Linksys G650 also worked, though needed a little tweaking.

---

### Post by samda on 2004-11-04
does anyone know how to get a Netgear MA521 to work with ubuntu? (first time on linux for me)  :-?

---

### Post by dubdubdub on 2004-11-08
I have a motorolla 802.11g PCI card. It shows up in Device Manger as "BCM94306 802.11g) but says devices and capabilities are unknown. Anyway to get this to work?

I swear I had to dig in the basement for 20 minutes just to find a cat5 cable. Now I am sharing internet from my G4 through ethernet with an airport supplied connection.

---

### Post by shad0w on 2004-11-08
[QUOTE=dubdubdub]I have a motorolla 802.11g PCI card. It shows up in Device Manger as "BCM94306 802.11g) but says devices and capabilities are unknown. Anyway to get this to work?

I swear I had to dig in the basement for 20 minutes just to find a cat5 cable. Now I am sharing internet from my G4 through ethernet with an airport supplied connection.[/QUOTE]
 I had a linksys 802.11b something, and it's worked with no problem.

---

### Post by dubdubdub on 2004-11-08
Thanks for the info. I have been digging around and it looks like I have to go drop another $50-$75 on a new wireless card.

I just built this PC a month ago to play Doom 3. Wish I would have known then what I know now.

---

### Post by chet on 2004-11-11
Are there any instructions on how to get the Netgear WG511 workng, do I need to pactch anything or is it just the case of downloading prism54 and installing it

Thanks

Chet

---

### Post by anklator on 2004-11-11
[QUOTE=chet]Are there any instructions on how to get the Netgear WG511 workng, do I need to pactch any5ork out of the box with ubuntu, anyways i had problems with mine in the beginning, but now it works fine, the card is a smc 2835

---

### Post by andy_sp1ke on 2004-11-14
[QUOTE=Jspired]The Netgear WPC-11 (V 3) was plug and play for me; worked out of the box.[/QUOTE]

So if I buy a netgear WPC-11 V3 card it should just plug into my unbuntu laptop and work? At the moment I have a belkin card and its RUBBISH! I've tried ndiswrapper and that failed, it just refuses to work :( How do I know if I am buying a version 3 card?

Andy

EDIT! do you mean Linksys WPC-11? I cant find a netgear one.

---

### Post by Jspired on 2004-11-14
[QUOTE=andy_sp1ke]

EDIT! do you mean Linksys WPC-11? I cant find a netgear one.[/QUOTE]
Can't speak for the original poster, but I have a Linksys WPC11 (v.3) and it worked out of the box.

---

### Post by andy_sp1ke on 2004-11-15
Ok, and that was just on a standard ubuntu box? I shall order one of those! and if it doesnt work i'll, i'll, i'll oh i'll probably just cry! :p

Andy

---

### Post by Jspired on 2004-11-15
Yep.  It's on a Toshiba laptop to be exact.

---

### Post by log on 2004-12-25
I have a WG511 netgear and ive been trying to get it going for days. oh well

anyway, I found the firmware and put it as /us/lib/hotplug/firmware/isl3890

but it doesnt work :(

any help would be appreciated.  :-k

---

### Post by log on 2004-12-25
sorry for double posting but here is what happens (in dmesg):

eth0: uploading firmware...
eth0: firmware upload done, now triggering reset...
eth0: device soft reset timed out

then lots of "eth0: mgmt tx queue is still full"

 :-?

---

### Post by makr0 on 2005-03-08
I have a netgear wg311, that I can't get working. Odd thing is that my first attempt at installing Ubuntu, it picked up the card easily and I was even able to connect to my network, due to some issues with the CD I was using I had to re-do the install process with a proper cd. but after that first time Ubuntu has refused to use that card. I can see in the device manager but thats it. I've re-seated the card and also re-installed windows to verify that it does still work. anyone have any ideas?

ALSO it detects my card as an ACX 111 54Mbps Wireless Interface.

thanks for the help

---

