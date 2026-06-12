---
title: "ADSL USB Modem drivers"
date: 2009-04-06
forum: Hardware
---

### Post by m0v3 on 2009-04-06
Hi. 

I have an ADLS USB modem Conexant Access Runner ACORP 9WAUC, and I'm trying to connect it using Ubuntu. I'm new at this OS , so I don't know barely anything. After a long search i have found [THIS]("http://www.ubudsl.com/en/start.php") soft , which led me a little further (any attemt to install drivers by hand failed) . So this program installed smoothly , then after a few steps asked me to plug in modem. After that it has found it ( found a cxacru modem) ant finished the configuration. Then i rebooted PC , and tryed to run the application . When I plugged the modem again , it responded and said that the modem was found. After that it tryed to synchronise it with server, but that thing failed. It seems the modem isn't even trying to find the provider's server, LED , which is responsible for it , doesn't even blink. Can anyone tell me what can be wrong ? I would appreciate every help , thank you.

---

### Post by 0cton on 2009-04-06
it may sound silly but are you sure the cables(ADSL, ethernet) are properly connected?
many (modern) modems connect to the server without needing to be pluggen to a computer at all.

---

### Post by m0v3 on 2009-04-06
This is an ADSL modem , which connects just if you plug it into some sort of OS.  I'm using it now in Windows , so it must be plugged correctly... When Windows starts , LED starts flashing time to time. It means it is trying to find the server. When the LED starts flashing continuously , it means that it has found the server and I can type in my Username and password to connect to the internet.

---

### Post by coffeecat on 2009-04-06
> **m0v3 said:**
> This is an ADSL modem , which connects just if you plug it into some sort of OS.  I'm using it now in Windows

Correction: not some sort of OS. Just Windows. Generally speaking, ADSL USB modems are cheap nasty skimped devices that only have Windows drivers. You'll find howtos for getting some of the more popular ones (such as Thomson Speedtouch) to work with Linux, but take it from me: it isn't worth the effort. Even if you get it working, USB is totally the wrong type of port for networking. It wasn't designed for networking and it slows a good adsl service down. You get no firewall in a USB modem, and you can't configure them for NAT - both useful security measures.

Do yourself a favour and chuck that thing away and buy yourself an adsl modem-router. It doesn't have to be particularly expensive, and it will work with any OS. You just configure the modem through a web interface with your ISP login and connection details, connect the router to the computer with an ethernet cable, and you're sorted. A modem-router will have a built-in firewall and you will be able to enable NAT. **And** you'll be able to connect more than one computer in order to share the single adsl connection.

I'd give the same advice to a Windows user. If you don't want to throw the USB device away, use it as a doorstop or as a paperweight.

---

### Post by m0v3 on 2009-04-07
I thought someone might say this :) My opinion gets as yours day by day , as i'm p***ed off with that modem. But I still want to connect it , as I'm working with a LAN of 2 PC's, and both of them have just 1 ethernet port :(

---

### Post by coffeecat on 2009-04-07
> **m0v3 said:**
> I thought someone might say this :) My opinion gets as yours day by day , as i'm p***ed off with that modem. But I still want to connect it , as I'm working with a LAN of 2 PC's, and both of them have just 1 ethernet port :(

But that's just the situation where an adsl modem-router comes into its own. Get a router with 4 ethernet ports (that's most of them) and you're set up nicely. Don't forget that a modem-router is basically a cut-down computer dedicated to serving a LAN. You only need one ethernet port per computer because they all become clients to the router.

All my computers, my NAS device and my network printer only have one ethernet port each and that's fine. If I need to connect more than 4 devices to the router via ethernet, I just use an ethernet switch somewhere.

---

