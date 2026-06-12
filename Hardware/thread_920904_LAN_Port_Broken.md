---
title: "LAN Port Broken"
date: 2008-09-15
forum: Hardware
---

### Post by masterfulchuck on 2008-09-15
I have an Acer notebook which is without a functional operating system presently because, after an update, wireless ceased to function (it's the Atheros 5007-- a pain), and it appears that my LAN port quit working at some point while I was using my wireless network exclusively.  Basically, I can't get the MadWifi driver working because if I try to compile the source (I have tried Ubuntu Studio, Ubuntu, and Fedora), I get an error about kernel headers. Ultimately, what I have is a computer without an internet connection, which, for my purposes, is not much of a computer at all.

What I'm definitely wondering now is what my options are.  I can spend hours painfully assembling all the necessary dependencies on a flash drive and hope to get the wireless card online, but I feel like those drivers will probably break in the future as they have in the past, and I will be in the same situation. I could replace the motherboard, but that seems expensive.  The notebook has an ExpressCard slot, so I could get a LAN adapter for that, but I am wondering about compatibility (I would really like to use Ubuntu Studio, if that makes a difference).  I have heard about USB LAN adapters, but, again, I am worried about compatibility.  Any ideas?

Thanks so much for your time!

---

### Post by ShawnDBruce on 2008-09-16
I'm sorry you're having 'net-access problems, but I may have a suggestions or two; first, try ndiswrapper, it uses windows drivers.  There IS the route of getting a cardbus wifi/lan card, but do you have the slots?  Anyway, that's about the extend I can think at it this time of the morning (7:17am.)  Good luck, and hope that wifi will run under ndiswrapper.

---

### Post by TheLions on 2008-09-16
before buying anything check if is Ethernet enabled in BIOS, and check the cable which you are trying to connect the PC with switch/router

also you can buy a external WIFI card whisch is 100% compatible with Ubuntu

---

