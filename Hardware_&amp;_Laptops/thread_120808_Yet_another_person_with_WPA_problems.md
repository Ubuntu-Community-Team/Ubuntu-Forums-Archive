---
title: "Yet another person with WPA problems"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by patrickweber on 2006-01-23
Yeah, I saw the Wiki.  I am currently reformatting and reinstalling ubuntu just so that I have a fresh pallette to work with, so I will give this a try again (previously I tried this after a few other ones, maybe wiping all changes will help).

And for the record, I do believe wireless is very immature technology but until I get my house wired, then I am stuck with either cables everywhere or wireless and since it's a laptop, I'd prefer the wireless.

---

### Post by patrickweber on 2006-01-23
Word to everyone else, with my configuration and with many other configurations I'm sure, this does work, just don't try to do this if you have done this or some other method.

I just reformatted and reinstalled Ubuntu and followed this and it worked like a charm.

---

### Post by patrickweber on 2006-01-23
It feels like I've exhausted every last solution to get WPA working on my ubuntu laptop.

My hardware:
Dell Inspiron 8500 running Ubuntu Breezy Badger.
Proxim ORiNOCO 11b/g PC Card (IEEE 802.11b/g PC Card; Model: 8470-FC)  Running Atheros chipset by the looks of it.
Netgear 54mbps Wireless Router WGR614v6

I have WPA-PSK enabled using my password.  I've tried NetworkMonitor (couldn't get the applet to show up), GTK-Wifi, Kwifimanager (I think that's what it's called), wpa_supplicant, ndiswrapper and nothing seems to work.

I've been through these forums all over the place but I still can't seem to find anything that will help me.

Can someone please point me to an article or an application or just very simply and easily tell menhow to enable WPA in Ubuntu with DHCP (I can do static also but DHCP is just a plus).

If it requires me reinstalling Ubuntu, sobeit, I just want WPA to work.

---

### Post by icheyne on 2006-01-23
Sounds like you've looked high and low already, but you didn't mention the wiki:

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

FWIW, I'm very disillusioned with wireless in general. It's immature technology and will wire my house up.

---

### Post by jml on 2006-01-25
I hope that I am not stating the obvious, but have you checked the WPA_Supplicant web site to see if your particular wireless chipset is supported?  I spent a week trying to configure an rt-2500 chip set only to discover it was not supported.  I also agree with you that wireless, especially encrypted wireless (either WEP or WPA,) is very poorly developed in Linux.  Its not the Linux developer's fault, however.  Most wireless card manufacturers are unwilling to "open source" their card's drivers.  That leaves the Linux developers playing catch up.  I would suggest voting with your dollars and refuse to buy devices that do not support Linux, and go the extra step telling the vendors and manufacturers why you did not buy their product.  If enough people did this, possibly, more vendors would support Linux.  End of sermon.;) 

Joe

---

### Post by icheyne on 2006-01-26
I would go further than that - wifi is rubbish on Windows too.

---

