---
title: "Deluge - need help"
date: 2008-08-17
forum: General Help
---

### Post by logos34 on 2008-08-17
Deluge newbie here--migrating from uTorrent and Azureus (bloat-monster).  

What is the correct firewall/port setting for Deluge torrent client?  I have it set for 'random' ...downloads go ok but uploads never start up.  (or is it that there are no other peers?)  Firestarter is lit up with blocked hits on the same port Deluge is using.  Do I need to unblock that port so I can seed?  I sure don't want to be a leecher...

BTW: where is a good third-party setup/config guide for Deluge?  Sorry, but the FAQs just don't cut it...I've googled in vain for one.

---

### Post by mb_webguy on 2008-08-17
If you're behind a router or firewall, you'll need to uncheck the random ports option.  That will give you a default port range of (I think) 6881-6891.  Open those ports on your firewall or set port forwarding on your router, just as you should have with uTorrent or Azureus, and you should see a fairly dramatic increase in your transfer speeds.

---

### Post by logos34 on 2008-08-17
> **mb_webguy said:**
> If you're behind a router or firewall, you'll need to uncheck the random ports option.  That will give you a default port range of (I think) 6881-6891.  Open those ports on your firewall or set port forwarding on your router, just as you should have with uTorrent or Azureus, and you should see a fairly dramatic increase in your transfer speeds.

yes, but [Deluge site ]("http://deluge-torrent.org/faq.php")says this:

> Generic BitTorrent   Which ports should I use?
  The official ports for BitTorrent are 6881-6889, but most ISPs block or at least throttle those ports, so users are encouraged to use a port range of something between 49152 and 65535.
 As for port forwarding, is this the right screen:
[ATTACH]81894[/ATTACH]

---

### Post by Elfy on 2008-08-17
Yes I think it should be that page, make sure obvioulsy that deluge and the firewall rule match.

---

### Post by mb_webguy on 2008-08-17
It doesn't look like you have the firewall enabled on your router, so you shouldn't need to do anything on that page.  What you're looking for is port forwarding, which your router calls "virtual server".  On the Virtual Server page, you'll need to pick a range of ports (such as the default 6881-6891 or something high like 65521-65531) and assign them to be forwarded to a similar range of ports on a specific IP on your network.  

This means that you also need to have a static IP for your computer, which you can set up on your computer using System->Administration->Network (click Properties for the network connection you're using, uncheck Roaming, and put in the static IP you want to use, a mask of 255.255.255.0, and the IP of your router as the default gateway).

---

### Post by logos34 on 2008-08-17
> **mb_webguy said:**
> It doesn't look like you have the firewall enabled on your router, so you shouldn't need to do anything on that page.  What you're looking for is port forwarding, which your router calls "virtual server".  On the Virtual Server page, you'll need to pick a range of ports (such as the default 6881-6891 or something high like 65521-65531) and assign them to be forwarded to a similar range of ports on a specific IP on your network.  

Is this the page and what do I put there:

[ATTACH]81900[/ATTACH]

Or do I want "special application":

[ATTACH]81901[/ATTACH]

>  This means that you also need to have a static IP for your computer, which you can set up on your computer using System->Administration->Network (click Properties for the network connection you're using, uncheck Roaming, and put in the static IP you want to use, a mask of 255.255.255.0, and the IP of your router as the default gateway).

'roaming' mode' is alrady unchecked...It's currently set for 'automatic (dhcp)' --I have wired pppoe dynamic ip adsl.  So what 'IP address' to use?

> configuration: static IP address
IP address: [COLOR=Red]?[/COLOR] 
subnet mask: 255.255.255.0
gateway address: 192.168.0.1

---

### Post by logos34 on 2008-08-17
> **mb_webguy said:**
>  and you should see a fairly dramatic increase in your transfer speeds.

btw, I downloaded ~300 MB flac files this morning at ~50 KB/s (on a 768 kbps adsl line), so isn't that a good rate?

---

### Post by mikewhatever on 2008-08-17
There is a site with guides on how to forward ports on lots of routers, DI-604 included. [http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-604/Utorrent.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-604/Utorrent.htm)

They didn't have Deluge in the list of programs, which is not surprising, but a guide for utorrent should do.

Edit: I don't think you have to do anything on the side of iptables. At least in my case, ports are open when deluge is running and closed when not, with any intervention.

---

### Post by logos34 on 2008-08-17
thanks.

I wonder if I shouldn't go back to uTorrent--seems lighter and simpler.  I don't do a lot of torrents (bandwidth challenged), but uTorrent (and Azureus) seemed a lot easier to configure.  It's just that I'd prefer a native linux (gnome) FOSS app, rather than azureus (with all that java crap) or a wine-dependant app

---

### Post by mikewhatever on 2008-08-17
What did you have to do to configure deluge that you did not while configuring utorrent and azureus? I think port forwarding is almost mandatory for a P2P application. They say you can use upnp instead, but that's a different story.

---

### Post by logos34 on 2008-08-17
whatever was the problem is now apparently fixed--I'm uploading in fits and starts...The reason it didn't before was simply there were no more peers.  I just finished one and it says 'seeding' but no one's out there so no upload activity (I have it set to '1.0' share ratio--only one torrent has come close to that).

This is probably not the best time for file sharing, with the Olympics on

---

