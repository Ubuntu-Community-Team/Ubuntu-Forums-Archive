---
title: "Recommend a PCIe WiFi card!"
date: 2014-09-11
forum: Hardware
---

### Post by S2005x on 2014-09-11
So, Just recently swapped to Ubuntu 14.04 and the USB wifi adapter I have isn't compatable. 

I ordered one on Amazon, and had to send it back because it's a piece of junk, and didn't work.

I'm using a temporary USB wifi dongle, that I don't want to keep tied down on this computer. 

I need an internal PCIe card for it. Preferably at $20 or less that will work with Ubuntu 14.04.

*Edit*

Please don't list the chipsets, I've seen the list of chipsets that work "great" with Ubuntu, but when I look for specific cards on Amazon or Newegg, I can't find the Chipset info every time.

---

### Post by QIII on 2014-09-11
Hello!

May be a little spendy, but check out the offerings on thinkpenguin.com.

Cheers!

---

### Post by S2005x on 2014-09-11
I did check those out. I found a nice one, but it was $35 shipped. 

I'm trying to find one a little cheaper, or maybe a free shipping coupon for thinkpenguin to bring it down to $29...

---

### Post by SeijiSensei on 2014-09-12
Intel 1000 pro cards are rock-solid in Linux.  Mostly they run about $30+ but here's a used one for under $9: [http://www.stikc.com/Intel-PRO-1000-MT-SINGLE-Gigabit-PCI-X-NIC-Dell-W1392-PWLA8490MT?utm_campaign=product-promotion&utm_medium=comparisonshopping&utm_source=googlebase&gclid=Cj0KEQjws8qgBRCLp-aploLbqcQBEiQAm0rD55ikKg__Ib7Qb9MWIXN9lgSM_4uFvnUZYClcbbhprooaAoqk8P8HAQ](http://www.stikc.com/Intel-PRO-1000-MT-SINGLE-Gigabit-PCI-X-NIC-Dell-W1392-PWLA8490MT?utm_campaign=product-promotion&utm_medium=comparisonshopping&utm_source=googlebase&gclid=Cj0KEQjws8qgBRCLp-aploLbqcQBEiQAm0rD55ikKg__Ib7Qb9MWIXN9lgSM_4uFvnUZYClcbbhprooaAoqk8P8HAQ)

Here's a new one at Newegg for $30: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833106121](http://www.newegg.com/Product/Product.aspx?Item=N82E16833106121).  What a discount! :D

---

### Post by S2005x on 2014-09-12
Those are both ethernet ports. I need a wireless card. It's much too far from the router to run a Cat5

---

### Post by weatherman2 on 2014-09-12
I use wireless ethernet bridges these days to put my desktop computers on the network when it's not possible to run a network cable.  I have used several PCI and USB wireless adapters in the past, and they can work well in some circumstances, but I find the ethernet bridges much more reliable and easy, especially because on the Linux side all you need is the wired connection to be working (plug your desktop computer into the ethernet bridge and it connects wirelessly to your router).  So, no wireless drivers to worry about.

If you can find an old router that is compatible with DD-WRT or TomatoUSB firmware, these both have "client" mode or "wireless ethernet bridge" mode built in.  Not all routers are compatible with these firmwares.  I am able to find cheap, decent 802.11n routers at my local thrift store, some of which work well for this.  Just check DD-WRT or Tomato compatibility before buying. I have had good experience with Linksys/Cisco E2000, E2500, E3000, and other routers on Tomato.

Another benefit of a wireless ethernet bridge: you can wake up your computer remotely via "Wake-On Lan" if you need to, something you can't do with a pure WiFi card.  Of course, the wireless bridge must always be plugged in and connected for that to work.

---

### Post by S2005x on 2014-09-12
I have 2 wireless routers laying around the house... 
Linksys EA2700
Netgear **WNDR3400v2**

---

### Post by weatherman2 on 2014-09-12
It looks like neither of those routers has Tomato support.  But both have a version of DD-WRT that works - maybe.  On some routers, installing DD-WRT is extremely easy (just download the firmware then do "Update Firmware" in the router).  With the EA2700, at least, it may not be quite that easy:

[http://forums.redflagdeals.com/linksys-ea2700-dualband-router-dd-wrt-support-finally-available-1426129/](http://forums.redflagdeals.com/linksys-ea2700-dualband-router-dd-wrt-support-finally-available-1426129/)

(Read the whole thread - there is at least one "how to" guide for flashing this router.  Follow those instructions carefully.)

One downside to DD-WRT on this router: although this is a dual-band router, it seems this version of DD-WRT doesn't support 5GHZ on this router, so you'd be able to use it only as a 2.4GHZ (still 802.11n) client bridge.  But if it's just a spare router, you could at least try it and see how well it works for you.

If you want to explore the DD-WRT version for your WNDR3400v2 instead, do some googling.

---

### Post by S2005x on 2014-09-12
Cool! I'll have to do some reading! 

I'll probably just use the EA2700 and turn the WiFi radios off to just use it as a switch (if I can do it that way). 

Just to make sure I'm understanding this correctly, it can wirelessly connect to my primary router/modem (AT&T), and work like a switch/access point? Kinda like bridging?

(Also, can this router do this without loading other firmware?)

Another edit, looks like the **WNDR3400v2 can work as a wirless repeater with its stock firmware, will that work?**

---

### Post by weatherman2 on 2014-09-12
Yes, that's it almost exactly - except you are USING a radio in the EA2700 to connect to your primary router, so you can't shut it off.  In DD-WRT, I assume that the 5GHZ radio either won't show up at all or will be disabled.  You may have an option to choose "bridged" (primary router assigns IP addresses to devices wired to the EA2700 ) or "unbridged" (EA2700 DD-WRT runs a DHCP server to assign IP addresses on a local subnet - like a router).  I prefer "bridged" so everything is on one subnet, printers can be shared, etc.

---

### Post by S2005x on 2014-09-12
That's how I have it set up right now. 

I have 3 routers all hard wired together in various rooms around the house. The main router/modem combo is the DHCP, the other two don't issue IPs.

This will make 4 routers... haha. 

So, the WNDR3400v2 has a wirless repeater mode built in. Can I use that, and still use the lan ports on the router to "bridge" this computer?

---

### Post by SeijiSensei on 2014-09-12
Sorry! Here you go:

http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100010074%20600014290%20600082401%20600014297&IsNodeId=1&Description=Intel%20wireless&name=PCI%20Express&Order=BESTMATCH

---

### Post by uRock on 2014-09-12
I own this one's baby brother, the N13 and it worked out of the box with Ubuntu. Asus' web page says this one was supported with the older 2.6 kernels. I'd think it would work fine with the newer 3.* kernels as well. I just fired up the system that has the N13 card in it and it works with ubuntu 12.04. [http://www.amazon.com/PCE-N15-performance-Wireless-N-Transmit-interface/dp/B0053GR2YI](http://www.amazon.com/PCE-N15-performance-Wireless-N-Transmit-interface/dp/B0053GR2YI)

I see you have a lot of networking hardware. I am not sure if you've ever visited monoprice.com , but they have really great prices on all kinds of cabling. I have a small rack of Cisco routers and switches and that site made wiring a lot more affordable.

---

### Post by weatherman2 on 2014-09-12
> **S2005x said:**
> 
So, the WNDR3400v2 has a wirless repeater mode built in. Can I use that, and still use the lan ports on the router to "bridge" this computer?

I don't know.  Give it a try.

---

### Post by S2005x on 2014-09-12
Spent a couple hours trying to get that to work... no dice. 

I'm going to research the DD-WRT option you mentioned. :D

---

### Post by weatherman2 on 2014-09-12
Read the DD-WRT instructions carefully.  Flashing a router firmware can be dangerous and could brick your router if it goes wrong.  You need to choose the correct firmware to flash, one specifically for that router.  The link I gave you has a little menu of specific instructions for the Linksys router you have - I'd follow them.

---

### Post by S2005x on 2014-09-12
I got it working on the netgear :)

Now_ how do I configure it to work like a wireless switch?

---

### Post by weatherman2 on 2014-09-12
Here's one tutorial:

[http://tsengf.blogspot.com/2012/11/dd-wrt-client-bridge-mode.html](http://tsengf.blogspot.com/2012/11/dd-wrt-client-bridge-mode.html)

Note that people don't call it a "wireless switch" - the correct terminology is "wireless ethernet bridge" or "client bridge."

The trick is to give the client bridge the same wireless security as the original router - so if you use WPA2 + AES security on the main router, you need to use exactly that when setting up the client bridge.  It may take some trial and error to get it right.

You might also look at the subnet range you are using now with the AT&T router.  if it is using 192.168.1.1/24 then change the local subnet of the DD-WRT router to something different (like 192.168.2.1/24 ) so they won't overlap.

A good way to debug this is to plug it into a laptop and disable the laptop's wireless card and try to use the DD-WRT client bridge to connect to your network.  If it doesn't work, set a static IP temporarily on your laptop to say 192.168.2.2 (if you set the DD-WRT to use 192.168.2.1/24).  Then you can login to the DD-WRT router and see if it has connected wireless as a client or not and make changes.  Once it connects, remove the static IP from your laptop, disconnect, re-connect normally (probably DHCP) and let the client bridge assign the IP connecting wirelessly to your primary router.

---

### Post by S2005x on 2014-09-12
Ok, here we go.

Got it "working"

On the Windows 7 PC that I set all this up on, it worked fine. I was getting 16Mb/s ish. 

I hooked it into the Ubuntu box, and I'm getting awful speeds... 

[[IMG]http://www.speedtest.net/result/3756391417.png[/IMG]](http://www.speedtest.net/my-result/3756391417)

---

### Post by weatherman2 on 2014-09-12
Are the Windows 7 PC and the Ubuntu box in the same physical location?  Obviously, WiFi reception depends a lot on the position of the original router and the client and distance between them.  Even a few feet can make a huge difference (if say moving the client bridge puts more walls in the path between client and router, you should expect much worse connection speed).

Unless the wired network driver in Ubuntu is messed up (doubt it), there should be no difference at all in the connection rate between Windows and Ubuntu if you have the client bridge router in the same exact spot.  There is nothing in the operating system affecting the connection speed - it's all in the client bridge router.   In fact, if you want, you can connect two PCs at once to the client bridge and run the test on both of them.

I don't think OOkla's Speedtest is necessarily that accurate - but I tried it on my box that is connected via wireless bridge and on a box that is wired directly to my router.  The results are almost identical for me.  (Both Ubuntu boxes.)  Still, you should probably be seeing faster results than you are showing.

---

### Post by S2005x on 2014-09-12
There is a wall in between, and about 12 feet apart, but its now closer to the main router. 

I don't have a laptop or anything that I can hard wire to it to test :(

---

### Post by S2005x on 2014-09-12
Ok... no idea what is going on here... 

Didn't change ANYTHING. For some reason, my AT&T Gateway lost connection and reset.

Now I'm getting this:

[[IMG]http://www.speedtest.net/result/3756420710.png[/IMG]](http://www.speedtest.net/my-result/3756420710)

---

### Post by weatherman2 on 2014-09-12
WiFi connectivity is highly susceptible to radio interference, and speeds can vary a lot depending on the quality of your connection.  2.4GHZ bands are used by lots of equipment including not only WiFi routers but cordless phones, bluetooth, wireless mice, etc. - not to mention your neighbors' routers, if you can pick up any.  Sometimes changing the wireless channel helps (often channel 6 is the default and your neighbor's might also be 6, so moving yours to channel 1 or 11 can reduce interference).  Sometimes repositioning the router even a little can help (move it away from the wall if it's directly next to it).

But it sounds like you are connect.  I wouldn't get hung up on speedtest results and instead see how well it works on your desktop.  Is it usable?

---

### Post by S2005x on 2014-09-12
Indeed. I'm satisfied with it. It is up against the wall, and behind the monitor, so I'll reposition it. 

It does hang a little occasionally. Like when I'm downloading updates, or when PlayOnLinux went to download Wine. It sat at 0% for a LONG time. I walked away, and when I came back it was done... : |

---

