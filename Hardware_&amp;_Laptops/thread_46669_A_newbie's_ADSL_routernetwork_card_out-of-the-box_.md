---
title: "A newbie's ADSL router/network card out-of-the-box fantasy"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by MarmiteMonkey on 2005-07-05
I have two PCs in my house -- an old one running Windows 98SE, and a newer one (my main PC) running Windows XP and (as of this morning) dual-booting with Ubuntu. Each PC connects to the internet (one at a time) via its own internal PCI ADSL modem card (with a Conexant AccessRunner chip).

My first goal is to get Ubuntu connected to the internet via ADSL on my main PC. I've seen some threads in this forum and elsewhere which discuss getting Conexant PCI modems to work with Linux, but all of that seems very long-winded and fiddly and I don't want to have to compile and recompile the kernel every time a new version of Ubuntu appears (I'm assuming I'd have to do this in order to stay up-to-date but haven't researched this fully).

What I want to do, therefore, is to get a stand-alone ADSL modem/router with wireless and ethernet support, and a PCI ethernet card for the PC. At a later date, I intend to get either an ethernet or wireless card for the other PC (and hopefully revive it a little by replacing W98 with some flavour of Linux), and I also want the option of getting a cheap-and-cheerful laptop which will run Ubuntu and connect wirelessly to the router. Eventually I want to be able to migrate my main computer usage from XP to Ubuntu, with the ultimate aim of ditching XP completely.

So, for phase 1, I am looking at the following hardware:

- a modem/router like this: [NETGEAR DG834G](http://www.ebuyer.com/customer/products/index.html?rb=8670208189&action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=52244)

- and an ethernet card like this: [3Com Etherlink XL 10/100 RJ45 Network Interface Card](http://www.ebuyer.com/customer/products/index.html?rb=8671827180&action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=27286) 

I've given these examples (without having researched either item very much) because they have good reviews on eBuyer and because they're made by well-known manufacturers and so are likely to be supported by major Linux distros. However, as well as being a Linux novice, I am similarly inexperienced in ethernet and wireless computer communications, and could have got the wrong end of a stick or two.

What I would like to know, please, is, am I being over-optimistic to expect that I will be able to connect my (Ubuntu-running) PC to the internet via ADSL more-or-less out-of-the-box with this kind of set-up? Of course, I'm expecting to spend some time fiddling about with the settings in terms of feeding the software with the kind of connection information that's provided by my ISP, and then a little more time setting up encryption passwords etc., but I don't want to have to think about recompiling anything or spending hours tinkering with variables in a text file in the hope that a magic combination of settings might work. I have no problem with following a set of instructions (even a long set of instructions) for a well-documented piece of hardware, but I don't yet feel confident enough with Linux, or with ethernet or wireless hardware, to have to work out very much for myself.

Am I imagining a sort of auto-detect paradise which I am never likely to see in reality?

If anyone could suggest a better combination of router and ethernet card, or a different hardware arrangement altogether, I would be very grateful. (Please give model names for each different bit of hardware so that I've got something concrete to look up.)

---

### Post by MarmiteMonkey on 2005-07-06
After nearly 24 hours, has no-one replied because the Linux internet hardware problem is so difficult? Or did I ask something inappropriate?

---

### Post by gnomeza on 2005-07-19
The ethernet card and ADSL router setup you're suggesting will work pretty much out-of-the-box.

Looks like the 3com card is supported by the 3c59x driver which is pre-built in Ubuntu Hoary (no messy kernel stuff to do).
 
It's likely that you can find an ethernet card which has better Linux drivers, though I'm not the person to ask about that.

Then once you've configured the Netgear router, all Linux sees is ethernet, so this is no problem.

BTW, I'm happy to help you out if you ever want to [get that Conexant ADSL modem working](http://ubuntuforums.org/showthread.php?t=1906). It doesn't require rebuilding the kernel. And maybe it'll get me to fix up the driver and submit it...or something.

---

### Post by damonw5 on 2005-07-19
[QUOTE=gnomeza]The ethernet card and ADSL router setup you're suggesting will work pretty much out-of-the-box.[/QUOTE]

Agreed. This way of setting it up is your best bet. The network cards should be auto-detected, and the router should come with idiot-proof instructions for its initial setup. I think you will be pleasantly surprised at how well the router setup works! As always, if there are problems you can ask for help here.

---

### Post by MarmiteMonkey on 2006-12-31
My very belated thanks to gnomeza and damonw5 for your replies -- I gave up on the thread after a few days and got on with the problem on my own. I am happy to report that, in the end, the installation was very quick and painless. I was particularly happy with the way that Ubuntu instantly recognised all my hardware.

---

