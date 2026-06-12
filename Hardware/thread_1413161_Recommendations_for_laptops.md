---
title: "Recommendations for laptops?"
date: 2010-02-22
forum: Hardware
---

### Post by pingu1 on 2010-02-22
Hi!
I may be buying myself a new laptop in the near future,
but I want to get a laptop that works without any trouble with Ubuntu 9.10.
I have a laptop already (HP), and this works fine, but I would like to get a newer and faster one, although this really is not a problem in Ubuntu. The "old" laptop runs fine, because Ubuntu requires so little to run and use.
 
Anybody got any recommendations? I just don't want to buy a new computer, and then find out that there is compatibility-issues with the WLAN, monitor, and so on, like I see some are struggeling a long time to solve. I had an issue with the WLAN on my computer, but I solved that one very fast.... I am hoping to get a computer , and get as little trouble with it as I can.
 
Anybody purchased a laptop, installed Ubuntu 9.10 - and everything worked flawlessly right out of the box? I have nothing against just adding some driver/codecs ets. in Synaptic Package manager, but if there is such a computer out there :) I would be greatful to hear about which one....
 
-Pingu1

---

### Post by pingu1 on 2010-02-22
AND: I would like it to have a good graphics card and a descent WLAN-card. :)
Or put in another way: A good computer, without costing my soul...

---

### Post by pingu1 on 2010-02-22
Nobody has bought a computer working nicely right out of the box with Ubuntu 9.10?

---

### Post by Nitewolf121 on 2010-02-22
Maybe read through this [http://www.linlap.com/wiki/laptops]("http://www.linlap.com/wiki/laptops")

The recommended laptop section hasn't been updated since September 2009 though.  But still might be worth checking out.

---

### Post by dondiego2 on 2010-02-22
Google is your friend "Linux Laptops"

---

### Post by Mighty_Joe on 2010-02-22
> **pingu1 said:**
> Nobody has bought a computer working nicely right out of the box with Ubuntu 9.10?

I have an HP (Compaq) 8510p that works flawlessly. I just got a new HP (don't have it at work, sorry) that won't even boot the live cd. I've tried all the workarounds (turn the fan off in the BIOS, *seriously*?) to no avail.  
Ubuntu has a [LaptopTestingTeam]("https://wiki.ubuntu.com/LaptopTestingTeam") but it doesn't seem to have newer models.  Your best bet is to go to your local retailer and chuck in a Live CD.

Edit:  My second laptop is an HP EliteBook 8530p.  It would not install from the Live CD but it installed fine from a Live USB drive.

---

### Post by pingu1 on 2010-02-22
So am I getting it right then, that if I run a live cd on a computer, it gets everything (including drivers) from JUST the Ubuntu CD, and it does not use any of the existing data on the computer? I am now actually while writing this, running one of my workcomputers on a Ubuntu 9.10 live-cd. 

So, if I am able to find a computer I would like to purchase, and they let me boot it up with a live-cd / and everything works - this means everything will work also after a full installation? I am just worried that linux live-cd maybe uses some of the drivers which already are installed? I guess this is a stupid hypothesis, but the question I am asking, really, is - IF the computer works flawlessly *monitor/wireless/ and so on* - then all of this will work in exactly the same way after fully installing Ubuntu 9.10? 

On this computer it seems, everything works using the live-cd and the lspci looks like this:

> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G94M [Quadro FX 2700M] (rev a1)
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
86:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
86:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
86:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 14)
86:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 14)
86:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev bb)
86:06.5 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ff)


AND: I did not install any drivers at all.... WLAN works, bluetooth, and probably the rest too.
I am surprised by the resolution I get (full resolution) from the live/cd. 

BOTTOM LINE: Everything works using a live-cd - everything works later after installing too?

---

### Post by pingu1 on 2010-02-22
can someone please answer? If something works running live-cd, it works after complete installation...?

---

### Post by Sef on 2010-02-22
> can someone  please answer?

Have patience.  Everyone here is a volunteer and at times it can take a while for help.    


>  If something works running live-cd, it works after  complete installation...?

It should work, but no 100% guarantees.

---

### Post by waynefoutz on 2010-02-22
My recommendation is anything that doesn't have  ATI graphics hardware in it. Stick with Nvidia, which is first choice, or Intel.

---

### Post by pingu1 on 2010-02-23
Ok. But I don't get why something which apparantly works running a live-cd - would not work after full installation? Why would something like that happen? 
(I apologise my inpatience... what can I say? I have kids and have lost the "patience"-gene....)

---

### Post by pingu1 on 2010-02-23
I ask concerning the live-cd testing, because - if I buy a computer/laptop, after testing it with a live-cd - and everything apparently works - and then I install Ubuntu 9.10 - and then all of a sudden something just goes dead - I am then stuck with a computer (probably expensive one) that has problems with hardware in Ubuntu....

So again - why would something turn out not to work, after working using live-cd? What are the reasons for this (potentially) occuring?
 
-Pingu

---

### Post by megamania on 2010-02-23
- Go out, choose the laptops you like among the ones with an Nvidia graphics card.
- When you have narrowed your choice to a few options, ask what wireless cards they have. 
- Run home, check if the wireless cards work with linux

Once you're there, you're pretty much done.

Just for information, I have an Acer 6930g and everything works under Ubuntu.

---

### Post by pingu1 on 2010-02-24
Thank you so much. Am I guaranteed that the graphics will be fine with Nvidia, no matter what?
If so - that makes me fall in love with Nvidia... :D

---

### Post by hxcobd on 2010-02-24
> **pingu1 said:**
> Thank you so much. Am I guaranteed that the graphics will be fine with Nvidia, no matter what?
If so - that makes me fall in love with Nvidia... :D

Absolutely not. As I speak, there's at least one thread on the first page of this subforum of someone having problems with their NVidia card.

I've had more luck with ATI than NVidia, personally. I don't know where that poster got the "Go with NVidia" opinion from.

A LiveCD really is going to be your best bet as far as seeing if everything works properly. If all the hardware works before actually installing, there's a 99% chance you'll be fine. The 1% failure rate is just a weird fluke situation that can't really be helped.

---

### Post by DownTown22 on 2010-02-24
I currently run Ubuntu 9.10 on my [[COLOR="Blue"]_Asus M51_[/COLOR]]("http://ca.asus.com/product.aspx?P_ID=vehI4ghphaA91hRu"), as well as new Dell Netbook, both without issues.  Live CD worked on both and the install worked perfectly - after a few updates of course.

In my experience, I've found you can't go wrong with the Intel chipsets, Intel CPU and nVidia graphics.

---

### Post by michael2009 on 2010-02-24
> **pingu1 said:**
> can someone please answer? If something works running live-cd, it works after complete installation...?

I installed Ubuntu and several other linux based OS's on my old Compaq n400 laptop. No need for any extra drivers, I have even installed without an internet connection (several times). Just check your hardware compatibility on this forum if you have a problem.

Don't worry too much, you can always choose the option to install Ubuntu WITHIN your existing Windows system.

---

### Post by megamania on 2010-02-24
> **hxcobd said:**
> As I speak, there's at least one thread on the first page of this subforum of someone having problems with their NVidia card.

I've had more luck with ATI than NVidia, personally. I don't know where that poster got the "Go with NVidia" opinion from.

If you think that suggesting an ATI card for a laptop which is going to run Linux makes sense, well... I don't know where you got that opinion from.  :-)

To the original poster: at this point, my advice is to do some internet search and make an informed choice between Nvidia / Ati / Intel for Linux.

---

### Post by Speshio on 2010-02-24
This thread mentions a number of thin and light laptops:

[http://ubuntuforums.org/showthread.php?t=1393889&highlight=toshiba+t135-s1309&page=1](http://ubuntuforums.org/showthread.php?t=1393889&highlight=toshiba+t135-s1309&page=1)

---

### Post by pingu1 on 2010-02-25
Thank you so much guys. Informative answers. 
My worry is that I buy a computer, and then get stuck with 800x600 and no wireless :)

O.k. - I will walk around considering various laptops, check with a live-cd - and if I get a descent resolution and wlan... I am pretty much there, as you said, Megamania.

Thank you guys!

---

### Post by pingu1 on 2010-02-25
P.S.: I've been recommended Nvidia and Intel from a guy who's used Linux/Redhat/u-name-it linux distributions for numerous of years, so I sort of have now sort of verified your claims here...

---

### Post by Mighty_Joe on 2010-02-25
> **megamania said:**
> If you think that suggesting an ATI card for a laptop which is going to run Linux makes sense, well... I don't know where you got that opinion from.  :-)


Probably from experience.  I have two laptops, both HP's, with ATI cards.  They work fine with the default drivers. I haven't tried the restricted drivers.

---

### Post by megamania on 2010-02-25
> **Mighty_Joe said:**
> Probably from experience.  I have two laptops, both HP's, with ATI cards.  They work fine with the default drivers. I haven't tried the restricted drivers.
I never said ATI cards don't work. I have an Ati card myself on the desktop.

But if somebody asks for an opinion, I'd never suggest to deliberately choose ATI for a Linux laptop.

---

