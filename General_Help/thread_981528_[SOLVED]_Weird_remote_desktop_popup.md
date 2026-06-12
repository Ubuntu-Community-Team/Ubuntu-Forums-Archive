---
title: "[SOLVED] Weird remote desktop popup"
date: 2008-11-13
forum: General Help
---

### Post by Radioman991 on 2008-11-13
This was interesting....

In all the years I've been traveling,  I was minding my own business, surfin the net, and I get this popup saying a computer at ip address 10.x.x.x (whatever the IP was) wants to make a remote desktop connection to your computer. The IP is in the range assigned by DHCP here in the hotel. 

Some doofus here in the hotel must have been scanning for PCs on the LAN.  First time I have ever had that happen to my knowledge.  Thank God for Ibex, at least warning me.

I do not have remote login enabled.  Is there a service I can turn off that will disallow remote desktop requests permanently?  I have no need to have RD running on the company PC...when running Ibex.

Thanks

PK

---

### Post by bswilson on 2008-11-13
You're most likely looking at an attempt to connect using Remote Desktop Protocol (RDP), which listens on port 3389/tcp. 

You need to double check and ensure you have disabled this remote connection.  The How-To Geek has [a great explanation]("http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/") about this. 

To definitively make sure it doesn't happen, you will want to block the connection in the first place.  So your best bet is to block *all* incoming connections with your iptables firewall (which is built in on Ubunutu).  OK, maybe you want to allow incoming SSH or something like that... :)

If you have [Firestarter]("http://www.fs-security.com/") installed on your machine, this is easy to do.  Check out [their tutorial]("http://www.fs-security.com/docs/tutorial.php") on how to get it set up.

---

### Post by Radioman991 on 2008-11-13
Thanks dude.  Missed the Remote Desktop setting in System Preferences!

Kinda freaky though..makes you wonder how many other times when running Winders some yahoo down the hall scanning the network.  Shouldn't be surprised.  Yet another reason the next time Wifey gripes about all the PCs in the house running Ubuntu  :lolflag:

---

