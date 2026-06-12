---
title: "Network Connection Woes"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by superami on 2006-12-02
I have a Dell Latitude D620 Laptop, and I am having major connection issues under Ubuntu Edgy Eft.  Ubuntu Dapper Drake install hangs after only 82%, so its not even an option.

Basically Ubuntu recognizes the wireless and wired network adapters.  If only wired is enabled it seems to connect properly to my wired router.  However, when I try to access a website everything seems to work all right, I get a looking up connection, and connection, but then it just hangs forever at waiting for connection.  I never can actually get online.  At the same time, I can use SSH to access my server or other computers in the network without problem.  

The wireless network doesn't seem to work at all.  It cannot find any networks in the area, despite the fact that windows can.  

I also had the same problem with my previous laptop a Dell Latitude D610, and I ended up giving up on Ubuntu for that laptop.  And SuSE and Fedora both have mixed results with the network connections.

Does anyone have any suggestions?

---

### Post by euchrid on 2006-12-03
Don't know if this helps, but I've been having major problems with my wireless network (and still am).

I'm trying to link up 3 machines - a laptop, and old pc with two hard drives and a brand new pc with one hard drive. The pc with two drives is dual boot with Windows XP.

I am using 2 identical SMCWPCI-G Wireless cards and an SMC Barricade-g SMC7904WBRA2 Wireless Router.

I couldn't get the damn wireless card or router to be found anywhere with Windows, and Ubuntu on my two hard drive dual boot system wasn't working either; so I tried it out with the new pc, with a fresh install of Ubuntu 6.10 (Edgy). *That* worked fine; it found the card, and then found the router. Once I got the router set up, Windows, on the other pc, now recognised the card and router, and I could now connect to the internet on two PCs. 

However, Ubuntu on the dual-boot system still wouldn't find my wireless card. I had previously had to compile a new kernel to fix another, unrelated hardware issue; I tried out the old kernel, which was still on my system. It worked!

Now, I can't connect to the internet, it seems, unless I first connect with Windows, re-boot, and then start Ubunutu - apparently now working in old and new kernels! This part doesn't make any sense to me. When I find an answer, I'll put it here.

But what I surmise from the above is that the necessary drivers for my wireless card were in the kernel (2.17.x) shipped with Ubuntu Edgy, and the new kernel (2.18.x) (downloaded from elsewhere) did not have them. There could be a bunch of other stuff still conflicting, but it's looking like I might have to re-install Ubuntu to get this working fully. At least for the moment I can connect to the internet; it's just getting the computers to interact that's giving me headaches (and needing to run Windows first, even though *that* wouldn't be working without Ubunutu!)

I also found I had to make sure I'd set up my wireless card (once recognised) to run DHCP and type the ESSID name  (in Properties in Network). There was nothing else I needed to do, but I'm convinced the difference was in the kernel (drivers, I presume). Hope this helped in some way!

---

