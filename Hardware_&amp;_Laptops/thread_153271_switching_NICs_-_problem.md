---
title: "switching NICs - problem?"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by bionnaki on 2006-03-31
hello. I've been having internet disconnectivity issues. I dont think it has anything to do with ubuntu because I've had the same problem when Windows was on this computer. I've been in contact with my ISP and they say there is no problem with the line and all is well. They say maybe it's a hardware problem - I dont exactly buy that considering Comcast has a poor reputation, but I might as well troubleshoot.

I have an extra D-Link DFE-528TX | DL10038D PCI card laying around that is known to work. Will I face any trouble popping this in and taking out the card that my ubuntu install knows?

I am running breezy + xfce if that matters.

thanks!

---

### Post by 5-HT on 2006-03-31
If it's an intermittent issue the first things I'd check, as you did, would be the modem and line signals, but it seems like your ISP said there was no problem with the history plots on the modem.

There should'nt be a problem at all switching to the new NIC so long as it's supported (maybe check the [Wiki]("https://wiki.ubuntu.com/") to see if anyone has posted their results with your NIC)?

When you boot, if the NIC is supported, it should be configured automagically.


As an aside, if you have a router, another thing you could try to see if it's a NIC v. modem/line issue would be to try and ping the router when your net connection is down. That would be strong support that your NIC is not the cause of the issue.

HTH

---

### Post by bionnaki on 2006-04-04
ok thanks for the help. installed the card and after power-cycling the modem, all is well. online without any internet disconnectivity problems (like before).

one thing I had to do was edit /etc/iftab and manually put in the new card's mac. before I did this, "configuring network..." during reboot took forever.

just wondering if there are any other little modifications like this that I should do.

---

