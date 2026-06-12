---
title: "Help with installing modem"
date: 2004-12-22
forum: Hardware &amp; Laptops
---

### Post by voodoostevie on 2004-12-22
Ok I have a Gateway Essential 667 (I know lame machine to begin with). The modem is stated as a GVC 56K PCI Voice Modem (Red Owl)  which has the Conexant HCF chipset in it as per the Device manager under Ubuntu. I have successfully gotten the modem to work using the Linuxant driver however I cannot afford to pay the $ for the license to get it to work at the full potential of my  modem's capacity. So it's stuck in that 14.4 max B.S. that Linuxant sets it at. 

I was in one of the irc chats I frequently go to and someone asked me why I was not using ndiswrapper for this. At first I thought it would be pointless to use it, but he said it should work. Well, I tried and it failed. I was hoping someone here could help out.

Seeing that ndiswrapper used the Windows drivers, I grabbed the drivers for the modem through Gateway themselves for Win2K because that was the latest driver for that particular modem from what I could tell. There were 2 .inf files. I loaded the one with a higher number in it and I got a hardware present, fuzzy message when I ran 

ndiswrapper -l 


I uninstalled the driver and installed the lower number and it showed it as present. So I ran 

modprobe ndiswrapper

to load the module as it stated in the instructions at [thier instruction wiki](http://ndiswrapper.sourceforge.net/phpwiki/index.php/Installation) . And it gave me a prompt again which, to me that meant no error at first. Until I ran dmesg and saw the local driver had an error loading. I cannot cut and paste the message right now for I am not on that box. My windows box is not connected to it at the moment either so I am using the windows machine to type this out. SOMEONE HELP!!!!

---

### Post by az on 2004-12-22
Wireless cards windows drivers use ndis funtion calls.  This is why drivers that use those functions can work with linux ndiswrapper.  I am quite sure that conexant modems (or any modems, for that matter) have nothing to do with ndis functions.

You can get more details from the ndiswrapper sourceforge project page.

---

### Post by burlap on 2004-12-22
AFAIK ndiswrapper works only for wireless network cards (although I have seen one website where it was used to make GPRS modem to work). 

I've had some experiences with a conexant modem - all bad. The same - I can't afford the driver (if dollar keeps getting cheaper it might change), with 2.4 kernel it was possible to use the last free driver (search ubuntu forums to find a link), with Ubuntu kernel it doesn't compile (or I do not have enough patience). 

In fact, on my box I have a smartlink modem (with nice drivers) and a d-link wireless via ndiswrapper. The problem with conexant concerns my brother's machine - and modem is his only way to connect to internet...

---

