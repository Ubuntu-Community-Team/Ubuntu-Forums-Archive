---
title: "Network attached printer"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by trico on 2004-11-07
I'm trying to figure out how to attach an HP Deskjet 6800 to Linux...   This printer attaches either by Ethernet, Wireless, or USB.  I'm using wireless from a Linksys 802.11b access point.  Linux is attached to the hub via ethernet (wired).  

When I "add a new printer" and choose the network option, I get serveral choices, CUPS, Windows, LPD, and HP Jet Direct.  Any idea on which (if any) would be appropriate for this printer?

trico

---

### Post by bytecoder on 2004-11-07
I'd say try selecting 'Windows' first; although, it might be one of the others depending on how you connect the printer to the network.

---

### Post by Magneto on 2004-11-07
select network-hp jetdirect- enter the ipaddress/url address of the printer - select your driver from the list and print away
either that or choose cups and put in the url
no need to waste a usb port on this

---

### Post by trico on 2004-11-07
Is there some format for entering the host address?  I entered the ip address as "192.168.1.102" (no quotes) and got no response.

Also, the 6800 is not in the release of HPIJS installed with Ubuntu.  I think it's at 1.6 and I need at least 1.6.2.  I downloaded the source from the hp site and in there is a directory of ppd files.  When asked by the printer installation wizard, I pointed it to the  ppd file for the 6800.  It all seemed to work but the test page doesn't print.

trico

---

### Post by ahood on 2004-11-07
[QUOTE=trico]I'm trying to figure out how to attach an HP Deskjet 6800 to Linux...   This printer attaches either by Ethernet, Wireless, or USB.  I'm using wireless from a Linksys 802.11b access point.  Linux is attached to the hub via ethernet (wired).  

When I "add a new printer" and choose the network option, I get serveral choices, CUPS, Windows, LPD, and HP Jet Direct.  Any idea on which (if any) would be appropriate for this printer?

trico[/QUOTE]

I had a similar problem with my Samsung laser wireless network printer. The PPD file seemed to install okay, but the Print Test page wouldn't work. I eventually got it to work by selecting the Unix Printer (LPD) option, entered the IP address (nothing preceding the address) and entered a name that I made up (i.e., samsungqueue) for the Queue. It then worked!

I hope you figure it out and if so, post how you achieved success.

Good luck!

Alan Hood

---

### Post by trico on 2004-11-07
It's working.  Well, mostly working.

Here's what I did:
- downloaded HPIJS driver 1.7.1 from HP (the latest as of today)
- attempted to install using network - jet direct 
- the above appeared to install but failed to print, when I investigated it had the wrong driver. 
- tried to install again (pointing to the ppd file when prompted) and was told that the driver was already installed. 
- tried again, this time looking for the printer under the HP list, not there 
- logged off, logged on, tried again looking for printer under HP, not there 
- rebooted, logged on, tried again looking for the printer under HP - IT'S THERE!
- printed test page, it worked, printed from Open office, it worked, printed from The Gimp, it did not work. 

There appears to be a bug in all of this.  When you install a new driver it does not appear to get used by the printer object created.  To compound the problem, the newly install driver doesn't appear in the list of possible drivers untill the system is rebooted.

All in all, it appears to be working ok, except for the gimp. Perhaps gimp uses another technique for printing that requires a different driver.  I'll save that problem for another day.

Since someone said they had luck with Unix Printer (LPD) on another manufacturers printer I deleted the printer object and created a new one using Unix Printer.  It didn't work for the HP DeskJet 6800.  Deleted that printer object and recreated with the jet direct method and all is well.

trico

---

### Post by Magneto on 2004-11-08
> 
There appears to be a bug in all of this. When you install a new driver it does not appear to get used by the printer object created. To compound the problem, the newly install driver doesn't appear in the list of possible drivers untill the system is rebooted. 

the gnome printer interface is just a frontend for configuring cups- to make the driver show up without rebooting restart the cups daemon

cupsd restart

Although this feature is good for gnome and some endusers I dont care for it and I definitely don't like how the cups web interface is disabled by default. It did work for me without problems though- but it doesnt help users like you and adds a layer of obstruction between you and the software you are really trying to configure which is cups.

---

