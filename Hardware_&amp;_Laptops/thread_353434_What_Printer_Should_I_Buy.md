---
title: "What Printer Should I Buy?"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2007-02-04
Hello everyone, 
It's time to buy a printer for my Ubuntu box. Currently, I'm running 6.10, everything is supported extremely well. Nonetheless, I want to do my research and make an educated choice, and that's why I'm posing this question here. 
What printer should I buy? I want something 100% compatible, without any frustration--I just want to hook it up and I want to be able to start printing. 
I don't need colour, and I don't need anything new fangled or complicated; I just need to print in b&w. 
I'm looking for a somewhat economical laser jet and I trust the feedback from the individuals here. Anyone have any ideas?

---

### Post by pay on 2007-02-04
Theres [this](http://www.linuxprinting.org/printer_list.cgi) list which should get you started. I hear Brothers printers have good support.

---

### Post by drpaul on 2007-02-04
I found the Brother HL-5140 to be a good compromise between price & performance. Never had the slightest problem printing from any Linux distro or from Win XP.

Paul

---

### Post by RandomJoe on 2007-02-04
I have a Brother HL-5040 laser printer, purchased about 3 1/2 years ago.  I'm a pretty low-volume printer, but I'm still on the original toner cartridge!  This one doesn't have a network interface - the price jumped considerably to add that at the time - but I bought a simple print server to plug it into, and it lives quietly in a corner of the closet waiting for the occasional print job.

The linux-printing link above is where I spent a lot of time when I was selecting this printer.  I had considered an HP laser, but couldn't justify the cost for as little printing as I do...  If this one ever winds up dying, I'll certainly look to Brother first.

---

### Post by teejay17 on 2007-02-04
Okay I've been doing more research and I see that a Samsung ML-2510 is supposedly supported perfectly for Linux. Furthermore, the installation CD contains Linux drivers/support. So far this sounds awesome!
My local Staples has these printers, so that means they're readily available too. Anyway, I just wanted to see what other people's experience has been like with one of these printers?

---

### Post by haiku99 on 2007-02-04
I recently bought a Brother HL-2040 at Staples for $70 on sale and am happy with it, drivers were available from Brothers website and someone here wrote an easy howto on setup...

---

### Post by linux_believer on 2007-02-05
I own the Samsung ML-2510 and have yet to get it working under Ubuntu. That's not to say you cannot get it functioning.

---

### Post by teejay17 on 2007-02-06
> **linux_believer said:**
> I own the Samsung ML-2510 and have yet to get it working under Ubuntu. That's not to say you cannot get it functioning.
Really? Uh oh. Well I haven't bought it yet, and that's maybe a good thing. 
But from what I"ve read on various sites it seems to be pretty compatible, almost as simple as plug and play. Why would that be?

---

### Post by linux_believer on 2007-02-06
It recognizes the printer when plugged into the USB port. I load the linux driver provided by samsung on th cd. When I try to print the printer warms up and stops.  I'm sure there is something I am missing. I hope I can get it working because the printer is great

---

### Post by teejay17 on 2007-02-07
> **linux_believer said:**
> It recognizes the printer when plugged into the USB port. I load the linux driver provided by samsung on th cd. When I try to print the printer warms up and stops.  I'm sure there is something I am missing. I hope I can get it working because the printer is great
Yeah, I hope so too. I'm really interested in buying this model. 
Perhaps there's something already included in Ubuntu, when you go to add a printer, and you don't need the actual CD with the driver?

---

### Post by Earl108 on 2007-04-07
:confused: Hello 

I just installed ubuntu 6.0 Edgy Fit? and I can't seem to get my printer (samsung 2510) to work. when I first installed it everything was recognized but the driver it was pointing to was the 2550, so after about an hour or so I managed to find where the linux driver was on the cd but It seems i have missed something, because the printer doesn't do anything when I try to print a test page. And the print jobs section says job stopped for some reason. So a little help is definitely in order from some kind soul out there. Thanks in advance. I'll keep checking here for some solution.

---

### Post by Iowa Dave on 2007-04-07
Hey, teejay, glad to hear you are getting good results with Ubuntu!

I don't know about Samsung printers, but I'd like to echo the positive feedback from others about Brother.

My Brother HL-2070N, bought at the local Staples, works great with both 6.06 Dapper and 6.10 Edgy. It sits quietly on my network, conserving energy but always ready to print. 

One of the neatest things about Brother's HL-2070N is that it responds to Hewlett-Packard's sort-of generic printing method called "PCL 6". This means that you may be able to print without having to find and install Brother's drivers. Instead, when asked for the type of printer, choose HP. Then scroll down the list looking for "Laserjet Series PCL 6 CUPS". 

Please note that my experience with the printer is through the network, not attached to the USB port. If someoue out there can report on using PCL to drive this printer through the USB port, please add the information to this thread.

To make it work the way I'm going to describe, you need to know the IP (network) address of the printer.* With that information then you don't need drivers. Just tell Ubuntu where to find the printer, and ask it to use PCL.

1. In Ubuntu, go to System > Administrating > Printing
2. In the Printers dialog that opens, choose the menu item Printer > Add Printer
3. In the Add a Printer dialog, Step 1 of 3, set the Printer Type to Network Printer, and choose CUPS Printer (IPP) in the dropdown next to it.
4. Enter the IP adddress of your printer in the URI field. Just type the numbers and dots, i.e. 192.168.0.150
5. Click "Forward"
6. In Step 2 of 3, select HP as the Manufacturer, then scroll down the Model list to Laserjet Series PCL 6 CUPS. Don't click or change anything next to the word Driver. Click  "Forward"
7. On Step 3 of 3 give the printer a name, such as Brother_HL-2070N. Note: the Name field doesn't like blank spaces.  The Description and Location fields are optional.
8. Click "Apply"

If the Linux stars align, your new printer will appear in the Printers dialog box and be available to your applications. You won't have to restart your computer to use the printer, but you might have to restart any applications that were running during the installation before they will recognize the printer.

Hope this information helps.

Dave

* To find the printer's network IP address you can do one or the other of the following things:
a. look in your router's DHCP table, if it has one and you know how to access it, or
b. obtain a Printer Settings page by pressing the Go button three times. The IP address will be shown on there.

---

### Post by ramjet_1953 on 2007-04-08
It's hard to go past HP printers for Linux use.

HP actively support Linux and their HPLIP package does a great job.

Regards,
Roger 8)

---

### Post by r00tintheb0x on 2007-04-08
[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

---

### Post by 11hjpphty76lkjj on 2007-04-09
[http://hplip.sourceforge.net/supported_devices/index.html](http://hplip.sourceforge.net/supported_devices/index.html)

For reference.
A

---

### Post by tuque on 2007-04-12
I bought a Samsung CLP-600N network color laser because it was advertised as Linux compatible.
Bull.. 
Samsungs Linux driver is a very poor offering compared to the MS Windows version.  Most features with the windows driver are simply unavailable in Linux.
Not to mention the real pain in getting the Linux driver to even work in Ubuntu.
I can't do double sided printing other than printing odd pages first then even which is fiddly.
The print margins seem to vary from program to program. It often prints "off the edge" of the paper despite having the correct settings in the CUPS driver.
It prints color too faint, no way to increase the density of color prints.
When I need to print professional documents I have to do this with MS. That sucks :(

---

### Post by moixa on 2007-04-13
look at the supported language by the printer
Avoid GDS language, then you are pretty much safe

ps. GDS is a cheap protocol for Windows only

---

