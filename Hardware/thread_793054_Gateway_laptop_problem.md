---
title: "Gateway laptop problem"
date: 2008-05-13
forum: Hardware
---

### Post by bigmac_bb63 on 2008-05-13
Hi guys,
I have a Gateway laptop and I can't connect to a wired connection
through a router. 
Can someone give me some help on this I am not sure what to do?

Thank you for your help,

bigmac

---

### Post by loserboy on 2008-05-13
it should be something simple

can you test the connection with another computer or are you sure the router is working right?

and can you type this command in a terminal

> lspci

---

### Post by loserboy on 2008-05-13
oh and also check that you have your wired connection turned on in network manager

System>Administration>Network  (in gutsy)

---

### Post by bigmac_bb63 on 2008-05-13
Thanks loserboy,
I did what you said and it tells me that I have a Network Controller:
Broadcom Corporation BCM4318 [Airforce One 54g] 82.11g wireless Lan controller (rev. 02)

What else am I looking for it seems pretty simple to me. I just want
to update to hardy heron through this 4 port router.

Thanks for your help,

bigmac

---

### Post by loserboy on 2008-05-13
well that shows your wireless card, but I thought you were trying to connect via wire. what about your regular Lan card, not that there should be a problem with it, i'm just curious to make sure I don't miss anything.

---

### Post by bigmac_bb63 on 2008-05-13
Hi loserboy,
the router shows it connected to the router and I went into system-administration and then network and it shows roaming mode enables?

Do I need to do something in particular in regard to the tabs.
General/DNS and Hosts?

Also, multicast is disabled and I can't the icon with the two monitors
to configure my connection what else can I do?

Thanks,

bigmac

---

### Post by loserboy on 2008-05-13
try disabling roaming mode, then just seting it to DHCP, that should grey out the other stuff, but then you need to make sure put a check-mark on the wired card after you close that window.

also if you could post the contents of what lspci outputs that would help

again are you trying to connect via wired or wireless card

> the router shows it connected to the router  ?

---

### Post by bigmac_bb63 on 2008-05-13
Thanks loserboy,
the changing of the interface worked so far. I am not able to paste the information from lspci to here because it is on a laptop connected to the same router unless you know a command where I could do that?

Thanks, bigmac

---

### Post by loserboy on 2008-05-13
i'm not sure how to copy an output from another computer, but if you are saying that everything worked now then i guess it doesn't matter.

---

### Post by bigmac_bb63 on 2008-05-13
So far it changed the interface where there was no wired network available
I don't know how that happened because a minute ago we just had one?
Now, we don't. Maybe someone is doing something screwy?

How do I put the wired interface back in the connection?

Thanks, bigmac

---

### Post by loserboy on 2008-05-13
we need to identify your LAN card run lspci again look for something about ethernet controller, here what mine looks like

> 02:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)


---

