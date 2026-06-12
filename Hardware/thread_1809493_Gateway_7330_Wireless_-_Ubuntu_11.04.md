---
title: "Gateway 7330 Wireless - Ubuntu 11.04"
date: 2011-07-21
forum: Hardware
---

### Post by ryanscene on 2011-07-21
My problem is that my wireless is not working. I have followed the typical steps of System>Admin>Windows Wireless Drivers(Using NDISWrapper) and installed the Broadcom drivers listed on Gateways support site. The Gateway 7330 as listed in the title. I know this is an ongoing problem for many and I have searched with little to no success. I am fairly new to the world of Linux/Ubuntu so any simple solution with as little lingo as possible would really help me out. That is if it is possible and I just have to imagine that this can be solved. Thanks, Ryan.

---

### Post by gordintoronto on 2011-07-21
If you run Accessories/Terminal and enter the command:
lspci
it should list about 15 lines of output. One of them will contain "802." That is your wireless adapter. Please tell us what the line says.

It is no longer typical to use Ndiswrapper with Broadcom adapters. If you can temporarily use a wired connection and run "additional drivers," it might offer the Broadcom driver for installation.

---

### Post by ryanscene on 2011-07-22
Thanks for the reply Gordin. I ran the command and the type I have is the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). Turns out this is a fairly common controller that several people are having problems with. I used the Additional Drivers tool but nothing has come up. I do have a wired connection but it is very inconvenient. I have seen several fixes while searching Google but none have been anything detail oriented enough for a beginner like myself. Again any help will be greatly appreciated. I will try and provide as much detail to help solve as I can. Thanks again, Ryan.

---

### Post by Paradoxfox93 on 2011-07-22
Hi, check out broadcomm directly since they may provide mroe up to date drivers or drivers for different versions of windows than the one that shipped with your gateway (sometimes the 98 driver will work but yours shipped with vista, etc.).  You can also try compiling the latest version of the linux driver but let us know how ndiswrapper works for you.

I can't personally vouch for the program but it's there if it helps you  Otherwise you could look up the documentation for using ndiswrapper and put together soem strings of your own.  It's not bad practice for a newbie to introduce yourself to the command line.  When I first started with feisty and knew nothing about linux or unix compiling ndiswrapper from source and inserting the module was my first project for the first week I owned that gateway laptop.  Getting into this will still eb much easier for you these days and I think that's great.

Wireless support is much better now and my broadcomm worked out of the box.  It's odd that driver still doesn't work but hopefully ndiswrapper will work for you.

In other words, welcome to linux, welcome to freedom!

---

### Post by gordintoronto on 2011-07-22
> **ryanscene said:**
> Thanks for the reply Gordin. I ran the command and the type I have is the Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). Turns out this is a fairly common controller that several people are having problems with. I used the Additional Drivers tool but nothing has come up. I do have a wired connection but it is very inconvenient. I have seen several fixes while searching Google but none have been anything detail oriented enough for a beginner like myself. Again any help will be greatly appreciated. I will try and provide as much detail to help solve as I can. Thanks again, Ryan.

Were you connected when you ran Additional Drivers?

If the wireless card were working, would you know how to make the wireless connection?

I know there has been a suggestion to plug away with ndiswrapper, but in my view, this is such a wrong answer that I would suggest uninstalling ndiswrapper, to ensure it doesn't get in the way.

---

