---
title: "Netgear PS101 Mini Print Server Printing woes solved."
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by packetcat on 2005-04-28
OK, I'm real raw, this is only my third day running Ubuntu and Linux ever. These forums helped a ton to sort out things and I used them extensively, thanks. This is wrtten with new users like me in mind.  :) 

The biggest problem I had was to get my Ubuntu Linux machine to print to my Epson C86 through the Netgear PS101Mini Print Server which is attached to a Linksys router. There  are Windows machines also connected to the router for internet and print access, they print fine,  none of the machines are networked to each other.   I spent the last day and a half searching these forums and the web and trying countless settings to no avail. I'll show here what I did to get it to work and it's simple, very simple and maybe it will save someone some time since this seems a problem that some users have had.

( I started to type a long story about this here but I ramble too much so I'll just say what I did and anyone can ask later if it's needed)

Set up the printer with the Gnome printer setup, use Network Printer **Unix Printer lpd** Host should be the IP of the print server and Queue should be **L1**. 

Ok once the printer is set up try a test page if it doesn't work do this. At the terminal:

  gedit /etc/cups/printers.conf

and it should look like this...

```
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Wed 27 Apr 2005 11:40:34 PM EDT
<DefaultPrinter Stylus-C84>
Info Stylus-C84
DeviceURI lpd://192.168.1.20/L1
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

```

... make sure the line starting with DeviceURI looks like this


**DeviceURI lpd://serverIP/queue**

in my case 
DeviceURI lpd://192.168.1.20/L1

The important thing is that it is** _lpd_** and that the queue is set to **_L1_**

If it doesn't edit it directly.

...at a terminal:

 sudo gedit /etc/cups/printers.conf

...at a terminal:

 sudo /etc/init.d/cupsys restart

...to restart cups

This is the only thing that worked for me. I'd swear that I tried that setting before but it wasn't until I added the line as shown above directly to the printer.conf and rebooted cups that it started working. Printing then started working from the test in the printer applet, gedit, Abiword and Gimp so it seems to be ok now.

I hope this helps someone..

---

### Post by Staesys on 2005-04-29
I wish I'd seen this earlier. It took me forever for me to get mine to work. I eventually found much the same information on a Red Hat forum and got mine set up.

server: 192.168.102.200
queue: PS-PORT_1

Works like a champ!

-Paul

---

### Post by scott1 on 2005-05-04
Thanks for the post.  Also worked for me.  I'm using a Brother 1440 attached to the print server port on a D-Link router.

When I tried to add the Brother printer, the ADD PRINTER screen would freeze on me after entering the following ADD PRINTER  setup parameters:

Network Printer:  Unix (LPD)
Host:  192.168.0.1
Queue:  lp

The setup screen would freeze and not complete the printer setup.  So I entered a bogus CUPS ipp Device URI and then edited the printers.conf file per your instructions which solved the problem.  The test page printed fine.  I also had previously added the following line to the cupsd.conf file to ensure the network printer server port was being recognized by CUPS.  This edit was necessary for another Linux distro I tried (maybe SuSE?), but not sure that it is necessary for Ubuntu.  

I added the following line to the cupsd.conf file under the cupsd.conf subtitle: 
<Location />

Allow From 192.168.0.1

Hope this info helps someone else.  The LAN printer setups for Linux are definitely  too complicated (or at least too obscure).  Also, if you have a firewall installed, be prepare to open the printer server port.  Had to sort through this one when trying Mepis which installs a Guarddog by default.

Thanks again

Scott

---

### Post by rickwood on 2005-05-05
[QUOTE=scott1]Thanks for the post.  Also worked for me.  I'm using a Brother 1440 attached to the print server port on a D-Link router.

[/QUOTE]

I've also got a Brother HL-1440.  It seems to work well, but I do have one problem -- trying to print an OpenOffice spreadsheet in landscape mode.  For some reason, I get information printed in portrait mode on the top 1/4 of the page (it almost looks like it's trying to print banner page or print job information or something).  Then the remaining 3/4 of the page prints OK in landscape mode.  Have you seen this on your printer as well?  btw, I'm using OOO 2, so perhaps this is contributing to my problem.

---

### Post by RonInSA on 2005-12-04
[QUOTE=packetcat]OK, I'm real raw, this is only my third day running Ubuntu and Linux ever. These forums helped a ton to sort out things and I used them extensively, thanks. This is wrtten with new users like me in mind.  :) 

The biggest problem I had was to get my Ubuntu Linux machine to print to my Epson C86 through the Netgear PS101Mini Print Server which is attached to a Linksys router. There  are Windows machines also connected to the router for internet and print access, they print fine,  none of the machines are networked to each other.   I spent the last day and a half searching these forums and the web and trying countless settings to no avail. I'll show here what I did to get it to work and it's simple, very simple and maybe it will save someone some time since this seems a problem that some users have had.

( I started to type a long story about this here but I ramble too much so I'll just say what I did and anyone can ask later if it's needed)

Set up the printer with the Gnome printer setup, use Network Printer **Unix Printer lpd** Host should be the IP of the print server and Queue should be **L1**. 

Ok once the printer is set up try a test page if it doesn't work do this. At the terminal:

  gedit /etc/cups/printers.conf

and it should look like this...

```
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Wed 27 Apr 2005 11:40:34 PM EDT
<DefaultPrinter Stylus-C84>
Info Stylus-C84
DeviceURI lpd://192.168.1.20/L1
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

```

... make sure the line starting with DeviceURI looks like this


**DeviceURI lpd://serverIP/queue**

in my case 
DeviceURI lpd://192.168.1.20/L1

The important thing is that it is** _lpd_** and that the queue is set to **_L1_**

If it doesn't edit it directly.

...at a terminal:

 sudo gedit /etc/cups/printers.conf

...at a terminal:

 sudo /etc/init.d/cupsys restart

...to restart cups

This is the only thing that worked for me. I'd swear that I tried that setting before but it wasn't until I added the line as shown above directly to the printer.conf and rebooted cups that it started working. Printing then started working from the test in the printer applet, gedit, Abiword and Gimp so it seems to be ok now.

I hope this helps someone..[/QUOTE]
Spent an entire weekend trying to come up with the right settings. Found this solution in 60 seconds - and it works like a charm for hp deskject 932C.

---

### Post by MotoWebmaster on 2005-12-10
Many thanks to those of you who posted and responded to this topic. I've been burning much of my free time working out this issue.

It seems that there are some bugs in the printer administration utility. Anywho here is my situation, and what I had to do to make printing work:

Printer: HP DeskJet 722C
Print Server: D-Link DP-300U
Print Queue: PS-439BD7-P1
Printer IP: 192.168.0.10

Here's my printers.conf file:

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sat Dec 10 15:12:00 2005
<DefaultPrinter DeskJet-722C>
Info DeskJet-722C
DeviceURI lpd://192.168.0.10/PS-439BD7-P1
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Then I changed my cupsd.conf file, removing the "deny all" statement and adding my printer server's IP:

## Restrict access to local domain
Order Deny,Allow
# Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.10

However, it still didn't work. So I checked the lpr log file and found that my printer driver, pnm2ppa, had a conf file of it's own that was crashing with an error on line 18. So I edited the conf file at:

/etc/pnm2ppa.conf

and commented out the plain "version" statement on line 18, and took a guess that it should be:

version 722

Then I saved it, restarted cups, and it finally worked.

I love Ubuntu, but that was way more complex than I've had to do on any distro.

---

### Post by rjz35 on 2006-09-04
Scott.

thanks worked like a charm

---

### Post by myname on 2006-09-20
Once again, these forums saved me countless hours!!!

Thanx!

--Kevin

ps.  I wish there were forums like this when I first tried to switch to linux about 5 years ago.

---

### Post by Michele Moglia on 2006-10-04
I want to ask you if are you using a PS101v1 or PS101v2 Printer Server, Netgear's website says that there two models and for the v2 says that this supports Linux.
I want to buy one but I found only a v1 and before to buy it I would want to be sure it's ok with my Ubuntu.

Thanks 

Michele

---

### Post by henryhynd on 2007-05-03
Just wanted to leave my thanks for this solution.

I had only been struggling with this for about half an hr b4 i found the article, but i don't think i would have figured it out by myself (i'm a noob ya see).

Well cheers again mate!

---

### Post by netreg on 2007-06-08
> **MotoWebmaster said:**
> Many thanks to those of you who posted and responded to this topic. I've been burning much of my free time working out this issue.

It seems that there are some bugs in the printer administration utility. Anywho here is my situation, and what I had to do to make printing work:

Printer: HP DeskJet 722C
Print Server: D-Link DP-300U
Print Queue: PS-439BD7-P1
Printer IP: 192.168.0.10

Here's my printers.conf file:

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sat Dec 10 15:12:00 2005
<DefaultPrinter DeskJet-722C>
Info DeskJet-722C
DeviceURI lpd://192.168.0.10/PS-439BD7-P1
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Then I changed my cupsd.conf file, removing the "deny all" statement and adding my printer server's IP:

## Restrict access to local domain
Order Deny,Allow
# Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.10

However, it still didn't work. So I checked the lpr log file and found that my printer driver, pnm2ppa, had a conf file of it's own that was crashing with an error on line 18. So I edited the conf file at:

/etc/pnm2ppa.conf

and commented out the plain "version" statement on line 18, and took a guess that it should be:

version 722

Then I saved it, restarted cups, and it finally worked.

I love Ubuntu, but that was way more complex than I've had to do on any distro.


Can i ask how you came to your Print queue name ?

thanks
Darren

---

### Post by john139 on 2007-08-19
Wanted to say thanks for all the info and guidance. Being new to Linux I'm in need for guidance.

OK. I had been printing from Linux to an HP LJ 4P using the hpijs driver using a SMB connection through a Win98 box acting as a print server. The Win98 box crashed and I bought a NetGear PS101v2 and it works fine from my WinXP box. I set the PS101 with a static IP (host 192.168.1.150, subnet mask 255.255.255.0, gateway 192.168.1.1) to simplify connections.

After reading this post and others I've connected to the PS101 in Linux using both Ubuntu and Kubuntu 7.04 fine using several connection types: LPD URI lpd://192.168.1.150/L1, IPP URI ipp://192.168.1.150:631/P1, and direct socket connection URI socket://192.168.1.150:9100. I've also tried several drivers: hpijs and ljet4.

I've looked at the files etc/cups/printers.conf and etc/cups/cupsd.conf and they look as expected. I've connected to the CUPS app using [http://localhost:631](http://localhost:631) and it looks good from there too.

The problem I'm having is when I print a test page I always get the same result that looks like ascii text of Postscript commands with many blank pages. The output is similar to "%!PS-Adobe-3.0<LF>%%Title: PPR Test Page<LF>%%DocumentNeededResources: font Helvetica" and so on. I've seen results like this in Windows when using a Postscript driver vs. a PCL 5e driver.

I see references to Ghostscript in Ubuntu. What gets me is the hpijs driver worked fine through the old SMB connection. Is this related and what could be a fix?

Thanks

---

### Post by Porpoise on 2007-09-16
OMG! I'm going round in circles with this one too!

This is my printers.conf:

<code>
# Printer configuration file for CUPS v1.2.8
# Written by cupsd on 2007-09-16 14:21
<Printer Business-Inkjet-2230>
Info PS0A6CCC_HP Business Inkjet 2230
Location SR_ENTERPRISES
DeviceURI socket://192.168.2.200:PS-PORT_1
State Idle
StateTime 1189948907
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
</code>

I still can't get it to print even a test page. Logging into the PS101 directly, I can print a test page from there and it prints fine from other machines on the network. I previously had it printing fine under Mandrake, so I can't understand why I can't get it to print on Ubuntu Fiesty!!! It's really doing my head in now.

Any help would be very gratefully received!  :(

---

### Post by Porpoise on 2007-09-18
Problem Solved!

It turned out I was trying to use the wrong printer driver!!  DUH!!

---

### Post by mmistroni on 2007-12-01
Hi,
 wish too i had seen this post earlier
it took me 1 min to get everything sorted...... after spending 3 hrs with problems over problems.....
thank you very much

regards
 marco

---

### Post by mmistroni on 2007-12-09
Actually, i can print test pages (from windows) but every time i try to print from some other applications (text editors, browser) i have 20 pages printed, all with (it looks like) postscript characters..... i cannot find out what's wrong...
coudl anyone help me out?

thanks and regards
 marco

---

### Post by jro on 2007-12-31
This thread helped me a bit but the problem was that I didn't have any Windows partitions to drop back to and running the Netgear Network config utility under Wine wasn't working (it kept complaining that the device name was incorrect). My main problem was that I didn't know the IP address of the PS101 since I had received it via Ebay and the original owner couldnt remember the IP he had assiged it.

I couldn’t get to its admin interface to set any configuration options, and to make matters worse, there was no factory reset button. My problem became, how do I find the IP of a device. My first idea was to do an nmap ping sweep of the devices’ last know IP range, but after two hours of scanning 65 thousand hosts this wasn’t turning anything up. I suspected that my friend had given it a class A private IP, but I wasn’t sure and I wasn’t about to try and scan 65 million possible hosts :-P

Then I got a second idea. First I downloaded Wireshark (formerly Ethereal) for packet capturing. Then I went into my vat-o-patches where approximately 72 million feet of cat5 patch cable call their semi-permanent home and found a crossover cable. I connected the two devices by the crossover cable, fired up Wireshark then plugged in the power for the mini print server. The first packet that came across gave me what I needed, the source IP of the packet (10.10.1.17). Then I changed my computer to be on the same subnet as the print server (10.10.1.5) and finally pointed a browser at 10.10.1.17. I was greeted by the web admin interface, and from there I set the IP to my subnet and to the configuration I wanted.

Oh, and make sure you set the device uri to lpd://device.ip/L1 or else it just won't work..

Of course this all would have been for not if there had been a password on the print server, I still have no idea how I would have reset that should I have needed to.. :-/

I hope this helps someone.

---

### Post by dayhawk4 on 2008-01-23
Had same combination of netgear ps101v1 print server with an hp laserjet 4p.  I used the solution offered, and it helped, but still from Gusty, I was asked to manually feed paper everytime I wanted to print something, the printer was continually being jammed, and it would wait between pages.  I found that just using lpd with the graphic cups interface seemed to work fine with system-config-printer.py 0.7.75.  The trick to getting things working correctly though was using the "HP LaserJet 4P Foomatic/ljet4" instead of the recommended printer driver.  It seemed to make all of the difference in the world...

---

### Post by Brerlapn on 2008-03-27
+1 Thanks

I don't know if packetcat is around anymore, but this saved me from an endless loop of messing with my printing GUI.  Worked like a charm.

---

### Post by phil.munck on 2008-03-28
I found this post after four weekends of effort.  It works with a NetGear WPGS606 Wireless Router with the wireless disabled which I am using as a print server plugged into a DSL modem/router.  The NetGear works with lpd://192.168.1.202/L1
Many thanks.

---

### Post by W4JKA on 2008-07-13
**Thank you!!!!**

Been fiddling with a PS121 for 2 days.

Had 8.04 about a week.  

John

---

### Post by 61811 on 2008-07-17
JRO, need your assistance please, or anyone else's.

Print Server: D-Link DP101
Problem: Don't have Windows98 or 2000. PSAdmin doesn't run on WinXP.
Background: 
(a) I do know the IP in the print server - 192.168.15.8.
(b) My Ubuntu and XP machines are not set with IP 192.168._15_.x, but with 192.168._0_.x.
Question:
How do I "point" any one of my computers (XP or Ubuntu) to this print server to access its configuration so that I may change its IP to 192.168.0.x? Can I connect that computer directly to the print server since there is a router in between with 192.168.0.x?

Thanks.

---

