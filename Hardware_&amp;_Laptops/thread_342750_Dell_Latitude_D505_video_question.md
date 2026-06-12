---
title: "Dell Latitude D505 video question"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by james.wilde on 2007-01-20
I have a Dell Latitude D505.  This appears to have dual Intel 82852/82855 video circuits with i810.  Both XP and Edgy indicate this.  I'm assuming one set is for the TFT screen and the other for the external video port/docking station output, since XP will not go higher than 1024x768 on the TFT but will allow 1280x1024 as soon as you couple in a monitor, either via the external port or a docking station.  Windows will also change between the resolutions automatically when one disconnects the external monitor.

What I'd like help with is to configure xorg.conf in such a way that it uses one configuration for the TFT screen and another for the external ports.  Trouble is, as you will see from my xorg.conf, it has 'generic' for almost everything.  What I presumably need is to be able to configure one instance of the circuits for the onboard TFT screen and the other one for the two external ports.

I attach my xorg.conf.  If anyone can tell me how to convert Device Manager to a text file, I'll send that, too.

Thanks in advance if anyone can give me a lead.

//James

---

### Post by james.wilde on 2007-01-22
Well, screen resolution is only one of my problems!  I discovered that my D-Link DWL 650+ card, which worked perfectly with a Netgear wireless router a couple of days ago would not even load properly when I wanted to connect to a Linksys.  At this stage I got the tiacx100c0D not found error, and spent a whole day trying to a) make the on board Dell Wireless circuits work or b) get the D-Link working.

During the course of this I upgraded to the A11 bios and lost most of my screen and the mouse functionality so I downgraded again to A09 and everything returned.

But I'm still using an old fashioned cable to connect to the internet.  I've found some very good sites which have tried to help but...

Pity, I'd love to be able to get rid of XP on this machine.

Thanks anyway, to those who read about my problem, even if they didn't have a solution.

//James

---

### Post by james.wilde on 2007-01-24
For those still following this exciting drama, I have the solution to my problem with the network card.  I entered the essid incorrectly as linksys, and not as linksys-g.  My non-functioning card started working again when I went to work and entered the essid there so I got suspicious and tested further.

So my one remaining problem is to find a way of specifying the two outputs, CRT and LCD in xorg.conf, so that the LCD uses maximum 1024x768 and CRT can go higher - how high, I don't yet know, but at least 1280x1024, and someone claims to have got 1400x1050.

//James

---

