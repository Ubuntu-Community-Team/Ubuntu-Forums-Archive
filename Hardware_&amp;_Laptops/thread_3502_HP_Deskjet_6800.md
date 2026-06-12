---
title: "HP Deskjet 6800"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by trico on 2004-11-06
I've setup and installed my HP Deskjet 6800 on my xp laptop, and now I'd like to install it to my Ubuntu Linux system.  The Deskjet 6800 is connected directly to my home's wireless network (no intervening systems, windows or linux) and I'm not sure what catagory it falls under when I do Computer->System Configuration->Printing.

I click on New Printer and Step one presents a choice between Local and Network printer.  Local appears to include parallel port and usb connected printers.  Network gives me the choice of CUPS, Windows Printer (SMB), Unix Printer (LPD) or HP Jet Direct.  The printer does have an IP address - 192.168.1.102 - so one of the network choices would seem to be the right thing to do.  The printer's controlling webpage allows me to set a Hostname, but there is no DNS on my little subnet so that doesn't seem like the right path.  Probably a fixed IP address.

I've looked around on the Hp website for some suggestions and haven't found any guidance.  

The HP Inkjet Driver Project looks promising, and does list the 6800, but I'm confused as to what to do with it.  It references something called HPIJS.  Looking in Synaptic, I see that it's installed on my system.  So I blunder forward, selecting HP Jet Direct, putting in the IP address for the host name and look for DeskJet 6800 under the drivers.  No joy.  

Do I need to download some newer version of HPIJS? Or am I heading off in the wrong direction?  (Or is it just not gonna happen?)

trico

Addendum:  I've fixed the problem.  The fix is descrived in a post titled Network Attached Printer.

---

