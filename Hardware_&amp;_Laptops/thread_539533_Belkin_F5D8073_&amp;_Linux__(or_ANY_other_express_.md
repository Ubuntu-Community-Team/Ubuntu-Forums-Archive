---
title: "Belkin F5D8073 &amp; Linux????  (or ANY other express card that works with Linux)"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by radnor on 2007-08-31
Hello to all!

I have a HP DV9420US.  I cannot for the life of me get the internal card working.  It is a Broadcom BCM4311 (rev02).  Went through all of the docs online, no joy :( .  Tried fwcutter, it does not have a MD5 check sum for my card, again no joy...

So, I'm looking into an EXPRESS CARD to put in the lappy.  Anybody use this card or some other express card?

TIA 
Radnor

---

### Post by mpstanard on 2007-11-07
I have this card and am having a difficult time finding instructions on how to install it with Ubuntu.

---

### Post by darrelltwo on 2007-12-04
THIS CARD WORKS!!!!! YAY! Right out of the box on Gutsy. I popped it in, put the CD in, copied the XP driver folder to my hard drive, then used the GUI NDISWRAPPER to load the driver. It could not have been easier! (well, I guess plug-n-play would have been easier)

Exact steps.
1) Put Card in computer.
2) Put CD in drive
3) Browse to XP Driver, and copy driver folder with all contents to your hard drive.
4) Go to ADD/Remove Programs and search for NDISWRAPPER
5) Load the WINDOWS WIRELESS DRIVERS Tool.
6) Go To SYSTEM, ADMINISTRATION, WINDOWS WIRELESS DRIVERS
7)Click on Install New Driver
8) Browse to XP folder and load *.INF file
9) You should then see the driver loaded and hardware present in the window.
10) Click Configure Network
11) Setup your wireless network info.
12) After all of that, you need to make sure you hit the checkbox that enables the wireless network.

You will not be able to configure the card from the network drop-down next to the TIME/DATE section of your tool bar. You will have to use the Windows Wireless Drivers tool for that. 

Hope this helps some of you newer guys, since this is way easier than compiling, sorting, and waving dead chickens over your head.

Darrelltwo

---

### Post by beerorkid on 2008-02-07
> **darrelltwo said:**
> THIS CARD WORKS!!!!! YAY! Right out of the box on Gutsy. I popped it in, put the CD in, copied the XP driver folder to my hard drive, then used the GUI NDISWRAPPER to load the driver. It could not have been easier! (well, I guess plug-n-play would have been easier)

Exact steps.
1) Put Card in computer.
2) Put CD in drive
3) Browse to XP Driver, and copy driver folder with all contents to your hard drive.
4) Go to ADD/Remove Programs and search for NDISWRAPPER
5) Load the WINDOWS WIRELESS DRIVERS Tool.
6) Go To SYSTEM, ADMINISTRATION, WINDOWS WIRELESS DRIVERS
7)Click on Install New Driver
8) Browse to XP folder and load *.INF file
9) You should then see the driver loaded and hardware present in the window.
10) Click Configure Network
11) Setup your wireless network info.
12) After all of that, you need to make sure you hit the checkbox that enables the wireless network.

You will not be able to configure the card from the network drop-down next to the TIME/DATE section of your tool bar. You will have to use the Windows Wireless Drivers tool for that. 

Hope this helps some of you newer guys, since this is way easier than compiling, sorting, and waving dead chickens over your head.

Darrelltwo

Thanks for mentioning this express card.  I tried everything I could, even different distro's and had no luck with my BCM4310 USB and dv2710us   Picked this sucker up from reading your post and this afternoon I was seeing my SSID.

I like how small it is.  Did not want to go USB incase I would bump it and rip the socket out or something.  The thing felt strange sliding it in, but it works.

Thanks

Sits back and waits for someone to figure out the BCM4310 USB days after buying this :)

---

### Post by emgram769 on 2008-03-08
> **darrelltwo said:**
> THIS CARD WORKS!!!!! YAY! Right out of the box on Gutsy. I popped it in, put the CD in, copied the XP driver folder to my hard drive, then used the GUI NDISWRAPPER to load the driver. It could not have been easier! (well, I guess plug-n-play would have been easier)

Exact steps.
1) Put Card in computer.
2) Put CD in drive
3) Browse to XP Driver, and copy driver folder with all contents to your hard drive.
4) Go to ADD/Remove Programs and search for NDISWRAPPER
5) Load the WINDOWS WIRELESS DRIVERS Tool.
6) Go To SYSTEM, ADMINISTRATION, WINDOWS WIRELESS DRIVERS
7)Click on Install New Driver
8) Browse to XP folder and load *.INF file
9) You should then see the driver loaded and hardware present in the window.
10) Click Configure Network
11) Setup your wireless network info.
12) After all of that, you need to make sure you hit the checkbox that enables the wireless network.

You will not be able to configure the card from the network drop-down next to the TIME/DATE section of your tool bar. You will have to use the Windows Wireless Drivers tool for that. 

Hope this helps some of you newer guys, since this is way easier than compiling, sorting, and waving dead chickens over your head.

Darrelltwo

I have tried this, and have gotten up to step 11.  There is no wireless network section (it only shows Wired Connection and Modem Connection), so I cannot set it up.  Maybe I am doing something wrong? Has anyone else had this problem?

---

### Post by beerorkid on 2008-03-08
I had to reboot with the card in and my ethernet cable unplugged for it to start working.

---

### Post by LuvSulime808 on 2008-03-09
I am running amd64 kernel... and i am having major trouble with this card... I have tried using the winXP32 and 64 bit driver, and the Vista... but nothing, I cannot connect... It says that the drivers are installed, but when I plug in all my details nothing... 

I'm also having issues with the compiling of native linux drivers...[PHP]
http://www.ralinktech.com/ralink/Home/Support/Linux.html[/PHP]

it uses the RA Link 2860 drivers... any help would be great!

---

### Post by grindbox on 2008-05-07
> **LuvSulime808 said:**
> I am running amd64 kernel... and i am having major trouble with this card... I have tried using the winXP32 and 64 bit driver, and the Vista... but nothing, I cannot connect... It says that the drivers are installed, but when I plug in all my details nothing... 

I'm also having issues with the compiling of native linux drivers...[PHP]
http://www.ralinktech.com/ralink/Home/Support/Linux.html[/PHP]

it uses the RA Link 2860 drivers... any help would be great!

I have tried several times to install 2 different usb cards (that work fine with the 32bit kernel) on the 64bit version of Ubuntu 7.10 and 8.04 with no success. I have tried every driver from vista 32/64 win2000, xp 32/64. nothing seems to work. So I am forced to run a 32 bit kernel on a 64bit box. Am I complaining? no, I love linux and 32 or 64 it outruns any windows machine. After seeing this post I am going to buy the belkin, although it is not dualband. is there any (known to work) dualband express cards out there? maybe thats a different thread... anyways:guitar:

---

### Post by beerorkid on 2008-05-07
I was a bit surprised at how few express cards are out there.

I can test out a live 64 bit CD if you like.

---

### Post by mehehool on 2008-05-16
hi my name is nick and i have a similar problem; i dont have the cd though if its possible could someone who has the cd please email me the .inf file 

[email]studd_oo@yahoo.com[/email]

---

### Post by beerorkid on 2008-05-16
gotcha bro.

expect a zip link here in a bit.

---

### Post by beerorkid on 2008-05-16
[http://www.beerorkid.com/blkn/](http://www.beerorkid.com/blkn/)

the inf, install folder zip, and iso are there.

---

### Post by lrbradford on 2008-07-02
Ok fellas.  I am running a dual boot Vista / Ubuntu 8.04 64 on a Toshiba A215-S7414 dual core.  I'm able to surf wired, but I gave up trying to get the onboard Realtek wireless to work with 8.04.  I broke down and bought the Belkin F5D8073 today, used the XP .inf file thru NDIS GUI, and I see the driver telling me the hardware is present (that's different).  I tried so many suggestions through this forum to get the Realtek to work, I wonder if something is amiss now?

I see a connection name eth0:avahi and tells me to get the administrator to help me out.  The problem is, I am the administrator.  ;-p

Any help would be apreciated.  I wonder if I shouldn't reinstall 8.04?  Is that the wussy way out?  I'm about game.  Soclose, and yet so far....

Thanks in advance,

---

