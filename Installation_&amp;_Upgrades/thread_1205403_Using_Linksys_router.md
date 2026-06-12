---
title: "Using Linksys router"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by hogey on 2009-07-06
I have googled this question and can't the answer for my specific situation.
I have a Linksys wrtg54gs wireless router. I can't figure out how to even access the internet after I connect the router let alone use the actual router. I'm lost any help would be appreciated.

I read in another post something about changing the wireless card to dhcp? Am I onto something how would I do this?

---

### Post by Sin@Sin-Sacrifice on 2009-07-06
Trying to connect from the wired machine or the wireless? What kind of ethernet adapters are you using for both wired and wireless? Are there drivers installed for them? Have you messed with anything in your router options?

---

### Post by memilanuk on 2009-07-06
Have you tried reading the [User Guide]("http://www.linksysbycisco.com/US/en/support/WRT54GS/download") for your router?  

I presume you have the basic information from your ISP necessary to connect to them such as username, password, and connection type (cable, PPPOE, etc.), DNS servers, etc.?

If you have a Windows or Mac client you should have an install CD that softens the learning curve a bit, but isn't really necessary.  

The router isn't going to have DHCP setup and ready for you until *you* configure it.

How you go about connecting to it depends on what kind of client computer (windows, mac, linux) you are using.  Basically the router is going to be waiting for you with a web interface at the ip address 192.168.1.1, with default username ' '(blank) and password 'admin'.  No encryption or nothing at this point.  Somehow you need to fire up the wifi connection on your client computer with an address on the same subnet, say 192.168.1.10, and connect to that web page.  Once you are logged in, you can go about configuring the router as per the user guide.  The one thing to keep clear in your mind is that there may be two forms of 'DHCP' you may be dealing with - one is the router as a DHCP client connecting to your ISP (depending on your connnection type), getting its network information from upstream, and the other is the router as a DHCP server for your internal network.  

Anywho, good luck.

Monte

---

