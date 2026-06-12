---
title: "Wireless Cards work with Netgear router but not with D-Link router"
date: 2005-11-21
forum: General Help
---

### Post by lasindi on 2005-11-21
It's very bizarre. I'm using the Netgear router here at home, and the D-Link router is being used at the apartment complex my dad owns. One of the tenants recently got a computer, but the Windows installation was completely screwed up and the machine didn't come with a Windows disk; fortunately they were open to trying out Linux.

I took the machine home, installed Ubuntu, and it works fine on my home network with the Netgear router. I've tested the machine with both a Netgear WG111v2 USB wireless card and a Belkin PCI wireless card.

However, when I brought the computer back to the apartment, it couldn't get an IP address from the D-Link router. It can detect the wireless network, but just can't get an IP address. This happens with *both* the Netgear USB card and the Belkin PCI card, which both work at home.

Unfortunately, switching the routers is not an option. I tried that, and another tenant's Windows 98 computer threw a fit. (I really don't want to touch Windows 98 unless I absolutely have to ;).) So, the D-Link router is there to stay.

The only difference I can think of between the routers (aside from the manufacturer) is that the Netgear router uses 192.168.1.x addresses and the D-Link router uses 192.168.0.x addresses. I don't see why this would be a problem (though I'm guessing that this is what threw the Win98  computer.)

If I can't get Ubuntu to work, they'll end up having to buy Windows. Any suggestions on how to fix this?

---

### Post by RAOF on 2005-11-21
If I remember correctly, DLink routers have problems with IPv6, which is on by default in Ubuntu.  It's possible that [disabling IPv6]("http://ubuntuforums.org/showpost.php?p=423242&postcount=4") will fix your problem.

---

### Post by suRoot on 2005-11-21
This sounds like MAC filtering to me.  Can you verify the access point isn't configured to only allow connections from specific MAC addresses?  Generally, when this is configured, your wireless card will see the SSID however you will not connect to the access point (and thus, never get an IP address).

In any case, it really sounds like a config issue on the AP.  Can you verify the settings on that end?

---

