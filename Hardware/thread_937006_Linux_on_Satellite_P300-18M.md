---
title: "Linux on Satellite P300-18M"
date: 2008-10-03
forum: Hardware
---

### Post by SifuFenix on 2008-10-03
Hi everybody,
Im planing to buy a Toshiba laptop Satellite P300-18M, and i need to install a Linux on it for my school. Im thinking about ubuntu distribution
and my questions are.. is this model fully compatible with Linux?

Processor Type	- Intel Core 2 Duo P8400 (Centrino 2) , Intel® PM45 Express chipset and Intel® WiFi Link 5100 
Clock - Speed	2,260 Mhz
RAM	- 3,072 MB
Hard Disk Memory	- 500 GB (250+250) certification : S.M.A.R.T. 
Display	- 17.0 Inch
Display Resolution	- WXGA+ (1440 x 900)
Graphics Chipset	- ATI Mobility Radeon HD3650
Networking	- Wireless LAN, Bluetooth
Operating System	- Microsoft Windows Vista Home Premium
Connection Ports	- 4 x USB 2.0, HDMI
Special Features	- Webcam, 5in1 Card Reader

thx

---

### Post by daUbuQ on 2008-10-03
I am using a Toshiba Laptop and it is working fine, however, still I didn't find the webcam drivers. Moreover, from toshiba web site you will not find any drivers for ubuntu. I recomment buying a laptop that have a pre-installed ubuntu such as Dell. Or if you want to have dual-system (two operating systems, windows and ubuntu), then you can buy this toshiba laptop and for any hardware that is not recognized you can search the internet for, I think you will find it. In my case, I just searched toshiba web site, and i didn't anywhere else because I never used my webcam.

thanks

---

### Post by mamber-m on 2008-10-03
Hello daUbuQ,

I am curious about your experience. Did you install linux into a Centrino 2 machine? I have a Centrino 2 Toshiba laptop (U405 with p series processor) and I was not able to install Hardy nor Intrepid (close to success in case of Intrepid).

It would be nice if you could outline what you did to install...

Thanks!

mamber-m

---

### Post by daUbuQ on 2008-10-04
Hello Mamber-m,

I am not that expert in Hardware in Ubuntu but I have some good knowldge in it. I have installed Ubuntu Hardy as a second Operating System from Ubuntu CD under windows Vista Busniess. All what I did if to follow the instractions and aftr I have restarted the system, windows boot menu appered and asked me which OS to start.

my laptop is a centrino Machine ..

I am using the following laptop
Toshiba Satellite Pro U300 
Technology :  type : Intel® Centrino® processor technology featuring Intel® Core&#8482;2 Duo processor T5750, Intel® Wireless WiFi&#8482; Link 4965AGN network connection and Intel® GM965 Express chipset
clock speed : 2.0 GHz
front side bus : 667 MHz
2nd level cache : 2 MB 



[http://gulf.computers.toshiba-europe.com/innovation/product/Satellite-Pro-U300-15B/145068/toshibaShop/false/](http://gulf.computers.toshiba-europe.com/innovation/product/Satellite-Pro-U300-15B/145068/toshibaShop/false/) 

Thanks

---

### Post by SifuFenix on 2008-10-04
Thx for the info but i have one more question
what about the L350 150, does Linux work on that one too?

Processeur	modèle : Processeur Intel® Pentium® double cœur T2390
fréquence d'horloge : 1.86 GHz
fréquence du bus (Front Side Bus) : 533 MHz
cache niveau 2 : 1 MB
Mémoire 	standard : 3,072(2,048 + 1,024) MB
mémoire maximale : 4,096 MB
technologie : DDR2 RAM (667 MHz)
Disque dur 	capacité disque (formaté) : 250 GB 
Contrôleur graphique  	Intel® GMA X3100 

I can simplifiy the question by just asking, you  what are the rulez concerning laptop hardware in general.. like for e.g i heard Intel stuff works well on Linux is that true, is that true?

---

### Post by mamber-m on 2008-10-04
I am not an expert (so help! some Mr. expert!), but the configuration you listed above seems "old" enough to run the current versions of Ubuntu (Hardy or Ibex) smoothly.

Possibly some exotic hardware (like fingerprint reader, webcam, Bluetooth, possibly wireless and wired network chip) might not work out of the box, but I saw a lot of information on the web about how to enable these kinds of non-standard hardwares, so even it might not work for the firts time, I think chances are you can find some info to make things work.

Good luck!

---

### Post by daUbuQ on 2008-10-05
I totally agree with mamber-m, I think ubuntu will work on that laptop but you will have to install all the drivers by your own.

I have just looked at the specification of the laptop you want to buy 

[http://gulf.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=150406&DISC_MODEL=1&service=AE](http://gulf.computers.toshiba-europe.com/innovation/jsp/SUPPORTSECTION/discontinuedProductPage.do?PRODUCT_ID=150406&DISC_MODEL=1&service=AE)


Thanks

---

### Post by IcarusR on 2008-10-05
Check out [http://www.linux-laptop.net/]("http://www.linux-laptop.net/") 
Listed links to peoples experiences with various flavours of linux on all makes of linux, 
with what works out of the box & how to get other stuff working.

---

### Post by Abu Linux on 2008-10-11
I have also just bought a P300 18m, and the best way to go, is to install a dual boot system so you can choose which OS system you want to run. 

Bear in mind that [*with the exception of the face recognition software for logging in without a password etc*] all of your hardware will work well with Ubuntu, and there are also so many comparable software packages you can add and install which will fully utilize your machines great capabilities.

The built in webcam should also work with Ubuntu. 

If you don't want to run a dual boot machine you can always intall virtualbox onto your Linux desktop, and then run windows from inside that as and when you need to.!

Good luck.

---

### Post by fotis_utmost on 2008-11-10
Hi,

I also have a toshiba p300-18m. I had installed Hardy but I had problems with ati, lan and wifi. For this reason I tried the beta version of Intrepid and everything work out of the box. Try a dual boot configuration to test Intrepid, but I am almost sure you won't face any problems.

---

### Post by shelterit on 2009-03-31
I'm using the P300 exclusively with Ubuntu 8.10, and the problems I've had are with reading xSD cards (which is common, and not just for this laptop) and the fingerprint reader (but next version of fprint I think handles this fine). The webcam, wireless, network, screens, anything USB, sound ... all works like magic.

Ok, a few addenums now 2 months later. I've upgraded to Jaunty 9.04 ([which wasn't painless]("http://shelter.nu/blog/2009/04/nightmare.html")) and the problems so far are ;

Can't get BlueTooth to work, although I suspect I had it disabled back when I had Windows on the machine, and the Linux drivers can't enable it. Same problem for my microphone(s), don't work, and I suspect I need to pop into Windows to enable them. 

Everything else seems to be fine, although I haven't got equipment to test HDMI, nor have I been able to test if the USB ports can charge USB equipment.

All in all I'm very happy with Jaunty 9.04 on my Toshiba Satellite P300.

---

