---
title: "Noob help: Wireless network card"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by dmateer on 2009-11-07
I am a complete Ubuntu noob, so please be gentle! I'm sure there is something simple I am overlooking because I'm trying to go something "the Windows way," but I can't figure it out.
 
I have a brand new install of Ubuntu 9.10. Where I live the ONLY internet access is wireless. (I am using a different computer to type this.) I have an Encore Electronics wireless card, ENLWI-G2. I found my way here:
 
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
 
... which led me to here:
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
 
.. which led to me to here:
[http://linux-wless.passys.nl/query_part.php?brandname=Encore](http://linux-wless.passys.nl/query_part.php?brandname=Encore)
 
... which says that my card will work with Linux. (Yea!)
 
I downloaded the driver from here:
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=1&Level=6&Conn=5&ProdID=36&DownTypeID=3&GetDown=false&Downloads=true)
 
And now I'm not sure what to do. I saved the file to my Ubuntu machine and extracted the files to my desktop. Then I read the ReadMe, which says to run some commands like "make" and "make install", etc. When I do that, however, I get errors. For example, when running "make" it says,
 
error: 'struct_net_device' has no member named 'hard_start_xmit' among other things.
 
What do I do?

---

### Post by dmateer on 2009-11-07
OK, here's an update: no idea what the error messages are about. When I rebooted, suddenly I have a wireless network available. Great! Except now...
 
1. About 25% of the time the wireless network will no longer be an option. What I mean is, there's no "Enable Wireless" option, and if I go to System > Administration > Networking Tools, the wireless interface is no longer there. If I reboot, it usually comes back. This same behavior occurs with either of the motherboard slots, so I doubt it's a motherboard issue.
 
2. When connected, it only stays connected for about 15 minutes to half-hour and then disconnects. I have a Windows laptop in the same room and the wireless stays on constantly, so it is definately not the network. The wireless card, put in my old Windows desktop, works fine. So it's not the card. After it disconnects, it cannot reestablish a connection until I reboot. Every 2-3 minutes it asks for the WEP key, but nothing happens when entered. I just get the spinning wheel of doom at the top.
 
Anyone have any ideas? I really want this to work out.

---

### Post by dmateer on 2009-11-08
Anyone...? Anyone...? Bueller...? :)

---

