---
title: "Will Ubuntu run on this mini-ITX, Skylake hardware? Want to check before buying."
date: 2016-07-13
forum: Hardware
---

### Post by multibot on 2016-07-13
Hi, here’s the guts of the setup:
CPU -   Intel Core i3-6100 3.7GHz Dual-Core Processor
Motherboard -   MSI B150I GAMING PRO AC Mini ITX LGA1151 Motherboard
(or other possible motherboards also with wifi,
Gigabyte GA-B150N Phoenix-WIFI Mini ITX LGA1151 Motherboard
or
ASRock H170M-ITX/ac Mini ITX LGA1151 Motherboard)

Also, for completeness:
Memory -   Crucial 8GB (1 x 8GB) DDR4-2133 Memory
Storage -   Samsung 850 EVO-Series 250GB 2.5" Solid State Drive
(also reusing spare Sata drives and/or buying new later)
Case -  Thermaltake Core V1 Mini ITX Tower Case
Power Supply -   Corsair CX 430W 80+ Bronze Certified Semi-Modular ATX Power Supply
(Wifi printer is Cannon Pixma MG5650)

 
There’s no graphics card as the machine is for learning programming and learning linux, and light trading and charting (i.e not heavy duty day trading). I’m intending to rely on the i3 built in graphics. It’s not for any type of gaming. Will put an HDMI monitor with this. (Similarly no sound card.)
 
- Will the wifi (on the motherboards) work reliably with no issues?
- Is it better, or more reliable, to use a Haswell processor instead of the Skylake generation?
- Will websites just work? Is that all OS independent?   e.g. video, broker/bitcoin exchange interaction pages
 
Bit nervous as a beginner about taking the plunge, but want to have a pure linux machine! Thanks.

---

### Post by Bucky Ball on 2016-07-13
Yes, it will, but considering what you want to do with the box, don't think that's your best choice. Stuff you'll never need or use.

I would go with a lighter flavour, perhaps Xubuntu, and add what you need via the package manager there, Synaptic Package Manager. Less bloat, faster install, faster user experience.

This is a good place to start for a beginner and will give a fairly gentle learning curve. 

With a bit more experience, I would have advised Xubuntu-core which would allow you to customise your setup more to only what you need, but the learning curve is steeper. 

While the hardware should have no problem with Ubuntu 16.04 LTS (five years support and use this release for Skylake CPU) I'd go [Xubuntu]("http://xubuntu.org/getxubuntu/").

---

### Post by multibot on 2016-07-13
Had a look at Xubuntu & looks interesting. (Forum didn't work for me earlier.) I may well use it, though I might pay around with other flavours just to familiarise and learn.

Good to know the hardware will work, which was the main worry, especialy the wifi internet and printer.

---

### Post by Bucky Ball on 2016-07-13
As mentioned, you'll get a better idea with a 'Try *buntu' live session running from install media. :)

There is an 'Install Ubuntu' icon on the desktop there, so if all is good and you're happy, you can take it from there. You might want to post a thread in Installations and Upgrades if you need assistance with installing. 

There are a lot of how-tos on the net, but just yell out if you get there and get stuck. ;)

Good luck with it and hope you are as happy with your first look as I was eight years ago. :)

(FYI: ALL the Ubuntu flavours - Xubuntu, Lubuntu, Ubuntu Mate and more - are based on the Ubuntu kernel (you can even install Ubuntu minimal ISO which is just the Ubuntu kernel). Therefore, you can 'mix and match'. 

For instance, if you install Xubuntu but prefer the Unity desktop environment used with Ubuntu, you can install it! Log out, choose the Unity session from the login screen, login and it will look like Ubuntu but have the Xubuntu default apps. 

And vice versa. Using Ubuntu but prefer the xfce4 DE (desktop environment) used by Xubuntu? Just install it and as above.

Both of these DEs and a whole lot more are available from the package manager, Ubuntu Software for Ubuntu (I think that's what it's using now) and Synaptic Package Manager for Xubuntu. Again, Synaptics can be installed in Ubuntu and ... on it goes! :) Have fun.)

---

### Post by Yellow Pasque on 2016-07-13
> - Will the wifi (on the motherboards) work reliably with no issues?
It would help if you could research and tell us what wireless chipsets the mobos use.

---

### Post by QIII on 2016-07-13
^^This.

And even still, OEMs can change specs at a whim and you might wind up with a different chip altogether -- one that may not work.  That's our lot as Linux users.

---

### Post by multibot on 2016-07-14
On the wireless chipset all I can find is that it's Intel, since it supports Intels HDTV interface WiDi. (I have no use for WiDi)
- Would that be because they don't want to be pinned down to one choice?

Anyway maybe it's better to chose an mboard without wifi and use a wifi card instead, to ensure it works, though I liked the idea of all in one. Or perhaps chose a mini-ITX board that's known to work with (x)buntu. How?


On the other hand the MSI has an M.2 connector. However I'm really confussed by M.2 and whether M.2 gives a big benefit compared to simillarly priced to SATA SSDs (£75 for 250Gb), or if you need the much higher priced units e.g. Samsung 850 Pro M.2 (about £150).  This says the Samsung Pro works with Ubuntu and Xubuntu, but there's too many variables for me to manage and it all seems a bit too bleeding edge for me at present:
[https://delightlylinux.wordpress.com/2016/04/21/ubuntu-16-04-xubuntu-16-04-and-the-samsung-950-pro-256g-m-2/](https://delightlylinux.wordpress.com/2016/04/21/ubuntu-16-04-xubuntu-16-04-and-the-samsung-950-pro-256g-m-2/)

(The MSI board support "Turbo M.2" whatever that is - Might be MSI marketing speak.)

Sorry, I'm thinking out aloud here really.

---

### Post by Bucky Ball on 2016-07-14
Just bought my wife an MSI laptop with M.2 slot. Nothing to be confused about or afraid of. It is a SATA SSD on a card, that is all. It just slots in, but you can't do work on the model I bought as it breaks the warranty (you can only replace optical drive bay, can't take back panel off, and couldn't work out how to anyhow).

One point about the M.2, though. You can get them in SATA interface or PCIe interface. The latter is lightning fast and astronomically expensive so you will probably be limited to the SATA version, which is absolutely speedy enough for day to day doings. The MSI model I bought takes either SATA or PCI M.2 cards. Their idea of a turbo M.2 probably means SATA or PCI.

An M.2, for all intents and purposes, will look to you like any other hard drive when you are accessing it from your computer. Run the operating system(s) from the M.2, use the HDD for data storage and the /swap partition (that was how it was done but not sure it matters a lot about the swap nowadays if you have a heap of RAM).

There are clips on Youtube showing how to insert M.2s. It takes about a second and is too obvious and easy. I'd see an M.2 slot, particularly one that is SATA and PCI, as an advantage, not something to be worried about. They simplify things, not vice versa. :)

(If desktops only used M.2 slots and not hard drive bays you could have terrabytes of storage in a regular sized desktop without issue. A hard drive bay would fit probably five or six M.2 slots and cards! Consequently, in probably a decade or less, we'll have terrabytes of storage on a desktop or laptop running M.2s and HDD/SSD we normally use now will be relegated to specialist storage use or be obsolete. Call me Nostradamus!)

As for the Samsung Evo 850 or the blah blah. Notice something? *They are exactly the same naming conventions as their SSD equivalents*. Same with the Intel and other brand models. Why? It is just a SATA SSD card, that is all. Of course it works on Ubuntu and Xubutu and any other OS you could name as it is a drive, an SSD, that is all, nothing more and nothing magical.

I bought the Intel 540 120Gb SATA M.2 and it was about AU$70, cheap, and runs like a rocket.

PS: Sorry about the lengthy post but I guess now you're across M.2s. There is a ton of info about them online if you want more.

---

