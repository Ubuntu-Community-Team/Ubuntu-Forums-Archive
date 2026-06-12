---
title: "Question about installing Ubuntu on HP Laptop (AMD + Radeon)"
date: 2011-11-09
forum: Hardware
---

### Post by drabina on 2011-11-09
I have HP G4-1215DX laptop with the following specs:

AMD 2.5GHz/1.9GHz VISION A4 Dual-Core A4-3300M
4GB DDR3 SDRAM
AMD Radeon HD 6480G

Yesterday I have tried to install number of Ubuntu releases (10.04, 11.04, 11.10). Mostly I was getting the black screen problem or system was hanging with a graphic card error. The only release that worked was AMD64 11.04 with the nomodeset.

Is there an option to get the latest 11.10 working with the Radeon card?

Thanks.

---

### Post by nismo9132 on 2011-11-17
> **drabina said:**
>  The only release that worked was AMD64 11.04 with the nomodeset.

Hi. I have the same laptop and have had the same exact issue. Thank you for posting this. I'll have to try 11.04 as I have only tried 11.10 which has given me the black screen/ system hang problem too.

---

### Post by drabina on 2011-11-17
What I did is I have installed 11.04 (AMD 64-bit version) with nomodeset and then upgraded to 11.10. Upgrade took couple of hours but everything worked just fine. Wish there was a cleaner option to install 11.10 than upgrading from older version.

---

### Post by nismo9132 on 2011-11-17
Alright. Thanks. Yeah that seems like it's not the best way to install it, but I think I'll give that a shot later today.
Thanks!

---

### Post by drabina on 2011-11-17
When you get Ubuntu installed, please post back if everything works on your laptop. My webcam, speakers, microphone, trackpad were all recognized and worked. The only problem was the video driver. For some reason it stated that VESA drivers were used though the performance was just fine.

---

### Post by nismo9132 on 2011-11-18
I installed 11.04. It seems to work, but I partitioned my HDD through Windows 7 and installed Ubuntu through the partition via CD.  I installed it with nomodeset and it seems to work great. Unfortunately, now when I boot it gives me the Ubuntu Boot Selector which I'm not a big fan of.. I prefer the simple text boot loader that Windows has. Also, since the Ubuntu boot loader is what loads, if I update to 11.10 and for whatever reason end up with the same blank screen problem, then I'm afraid I won't be able to even boot into an OS making my computer a paperweight.  I'm debating between just leaving Ubuntu 11.04, Uninstalling and waiting for a version that supports the A4-3300M and Radeon 6480G, or just uninstalling Ubuntu. I'm leaning towards uninstalling and waiting for a version that supports the hardware, but I'm still undecided.

---

### Post by drabina on 2011-11-18
Thanks for the update. Upgrading to 11.10 worked for me but YMMV. I understand your concerns with the boot loader. I did a fresh install of Ubuntu on a newly partitioned drive and still had this boot loaded pop up every time computer was booted. Kinda annoying.

Well, good luck with whatever you decide to do. Myself, I went with Win7 just because I am not that Linux savvy to deal with drivers, etc. I have to say though that Ubuntu looked a lot better than Windows.

---

### Post by nismo9132 on 2011-11-18
I started looking into how I would go about uninstalling it and from what I'm reading it's pretty annoying. I might just leave 11.04 on here just since I don't really want to deal with that aggravation lol.

Yeah, I have Ubuntu 11.10 on my 17" Dell Studio as well as Win 7.  It's a great OS and works perfectly on it (Core 2 Duo 2.1Ghz, Intel HD Graphics) so I was hoping this laptop would turn out the same but I guess not.  Best of luck with your g4.

---

### Post by rickle on 2011-11-26
Must be the Radeon Card
I just got a Gateway NV55S17u, 4GB AMD Dual-Core A4-3300M with Radeon HD 6480G 512MB Graphics card.
I'm trying to install 11.10 64bit.
I got it to run the install, using nomodeset=0, but cannot get to boot, I get a screen flash, some horizontal lines, then the Blank screen.
was going to try the 11.04 install, but while downloading the 11.04 version
I rebooted pressed e to edit the boot grub.
replaced quiet splash vt.handoff=7 with  nomodeset
It came up to the tty login, I logged in.
and ran sudo apt-get update && sudo apt-get install fglrx
rebooted and IT COMES UP GUI and all!

---

### Post by knock_ on 2012-01-22
Hi everybody, my laptop is Acer 7250 - AMD Dual Core E-350 4Gb Radeon HD 6310, I got ubuntu 10.10 installed and working with the fglrx driver, the only problem I have is with the performance of flash player video streaming in all browsers.

The installation was very simple but I couldn't do it with any of versions 11.x.

Cheers,

Carlos.

---

