---
title: "Built in media card reader (Toshiba laptop) NOT WORKING"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by kkarim on 2006-12-03
My Toshiba Satellite M40-185 has a built in card reader for:
-SD
-SmartMedia
-MS
-xD

I only really want the Memory Stick to work since it's what i use for my phone, and i have a compact flash pcmcia adapter for my digital cam's card.

here are the last 2 lines dmesg returns when i plug in and remove the card.
```
[17202809.600000] tifm_7xx1: ms card detected in socket 2
[17202817.144000] tifm_7xx1: demand removing card from socket 2
```

and these are the last few lines of lspci
```
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

```

I read a few guides on line, and tried to tinker around with it, and i know it has something to do with the Texas Instrument PCI7xx1 and the mass storage controller.. i just can't find what exactly... :/

I figured might as well cry for help... :)

Thanks in advance for any input you may provide me..

---

### Post by kmldqj on 2006-12-17
This might work for you:
[http://forum.ubuntu-fr.org/viewtopic.php?id=53509](http://forum.ubuntu-fr.org/viewtopic.php?id=53509)

The thread is in French, but you only need to understand the code part. It worked for me (Acer Travelmate 3000, the same card reader).

---

### Post by KLineD on 2006-12-17
Try this (in a console)
```
sudo modprobe tifm_core
sudo modprobe tifm_sd
```

And then insert the card... wait a sec and a dialog should pop up asking what to do with the card. If it works for you, add tifm_core and tifm_sd to the file /etc/modules so they load at startup

---

### Post by kkarim on 2006-12-17
well i'm pretty much fluent in french... i read the whole thread, and have already tried this... i just can't get it to work for my Sony memory stick.. maybe it's working for mmc or sd cards.. just not MS... :(

---

### Post by kkarim on 2006-12-17
thanks a lot btw.. this is the only usolved problem on my laptop...

---

### Post by KLineD on 2006-12-17
no prob. And yes I tried it with an SD card and a Sony memory stick, it works. The ones I can't read are those newer memory stick duo cards (using an adapter).

---

### Post by rykel on 2006-12-18
> **kmldqj said:**
> This might work for you:
[http://forum.ubuntu-fr.org/viewtopic.php?id=53509](http://forum.ubuntu-fr.org/viewtopic.php?id=53509)

The thread is in French, but you only need to understand the code part. It worked for me (Acer Travelmate 3000, the same card reader).

Hi Pals,

I am using a Toshiba M40, and I am so glad to come across this thread!

For as long as I can remember, since using Linux/Ubuntu, I have long classified my card reader as a "gone case"... but now I believe there is hope.

Anyway, I followed the French instructions to the letter, and now, my XD card is indeed detected. (see below)

[INDENT][B]$ dmesg
[17180018.488000] tifm_7xx1: xd card detected in socket 2[/B][/INDENT]

HOWEVER, there is no pop up icon on the desktop, like a USB drive, so how do I create that behaviour? That is, how do I access the info in my card reader?

Thanks for helping.

---

### Post by rykel on 2006-12-24
> **rykel said:**
> Hi Pals,

I am using a Toshiba M40, and I am so glad to come across this thread!

For as long as I can remember, since using Linux/Ubuntu, I have long classified my card reader as a "gone case"... but now I believe there is hope.

Anyway, I followed the French instructions to the letter, and now, my XD card is indeed detected. (see below)

[INDENT][B]$ dmesg
[17180018.488000] tifm_7xx1: xd card detected in socket 2[/B][/INDENT]

HOWEVER, there is no pop up icon on the desktop, like a USB drive, so how do I create that behaviour? That is, how do I access the info in my card reader?

Thanks for helping.

Christmas 2006 Surprise: I am glad to let you all know that 2 of my SD cards were detected AND mounted automatically, perfectly, correctly! (see screenshot)

---

### Post by petroskhan on 2006-12-28
I just came across this thread today, which is about one week after installing Ubuntu on my Toshiba laptop.  I am loving Ubuntu so far, but am having some minor problems, one of which is my built in SD card reader isn't reading SD cards.  I have looked over the information here, and tried some of it, but nothing is working so far.  Is there some thing more that needs to be done?  I haven't tried the stuff from the french website, since I can't understand the french parts, and I am paranoid about trying commands I don't understand, since I have had to re-install the OS three times so far after screwing up my video drivers.  Since I have a digital camera, I really need to get my SD card working, and would appreciate any help I could get.

---

### Post by thirdgen88 on 2007-01-05
My reader didn't work also (but was being detected, as seen with dmesg) on my M105-S3041, but once I loaded the tifm_core and tifm_sd modules (as mentioned above), everything worked perfectly... Try that first, and if that doesn't work, then maybe try that french web page...

---

### Post by rdroguett on 2007-01-07
read that !!

[http://skindley.wordpress.com/2006/11/24/fedora-core-6-toshiba-satellite-a105-s4284/](http://skindley.wordpress.com/2006/11/24/fedora-core-6-toshiba-satellite-a105-s4284/)

---

### Post by Zuuswa on 2007-01-28
```
sudo modprobe tifm_core
sudo modprobe tifm_sd
```

returns

```
FATAL: Module tifm_core not found
FATAL: Module tifm_sd not found

```

respectively.  Does anybody know where I can obtain these modules??  Or any other advice to get my card reader working.  I need it for the xD feature, however, and I dont particularly care if the SD, MS, MMC or SM readers dont work.

Thank you

---

### Post by whistlerspa on 2007-02-11
I tried this - the card loaded after the commands were run but 2 questions.

1. my files are called tifm_sd.c and tifm_core.c is this OK
2. I don't have a folder /etc/modules, shoulod i create one? - closest is modeprobe.d or modutils. I put the files in both folders but no joy on the reboot - the card was not recognised. What can i do now

---

### Post by whistlerspa on 2007-02-11
Ok got the SD card working by adding tifm_core and tifm_sd to the /etc/modules file after installing tifm-0.6b.tar.bz2 in /etc/modprobe.d as root. 

Ok so how do I get an xD card to work now

---

### Post by SonicTheHedgehog on 2007-02-23
> **whistlerspa said:**
> Ok got the SD card working by adding tifm_core and tifm_sd to the /etc/modules file after installing tifm-0.6b.tar.bz2 in /etc/modprobe.d as root. 

Ok so how do I get an xD card to work now

How do i "install tifm-0.6b.tar.bz2 into /etc/modprobe.d as root."?

---

### Post by liammoko on 2007-09-28
put in command in konsole with no responce. ](*,)
Toshiba satelite P25-s607
any suggestiuons
FF7.04

---

