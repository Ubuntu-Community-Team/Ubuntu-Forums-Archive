---
title: "compatible pci video card"
date: 2011-01-06
forum: Hardware
---

### Post by jack griffin on 2011-01-06
Hello to everyone and happy new year !
I am building a pc whose main purpose is to navigate the web and downloading files using aMule .
The motherboard is an elder (but fully functional) Asus P2B-D2 with dual Pentium III a 750 Mhz , 1 gb ram 
and integrated scsi support 8).
I planned to install Ubuntu 10.04 LTS on a 18 Gb scsi disc and adding an ide disc of proper size for data .
The main issue is that the onboard video card has 1 (yes, that's ONE!) Mb ram , and mobo does not have an AGP slot, just six PCI slots .
I booted Ubuntu 10.04 live cd after adding a S3 Trio64+ pci card (stone aged, I guess from 1996/7 , with some 4 Mb ram or so) .I've waited for ages , and ended up with a 800 x 600 resolution .
I need a card that will give a proper resolution on a 17'' monitor (1024 x 768 or higher) , I don't ask for fancy performance or 3d effects .
Question # 1 : does somebody else use a pci video card ? Which do you recommend ?
Question # 2 : do you think that the above configuration will run Ubuntu 10.04 properly , or should I install a less resource hungry distro (like CrunchBang or Antix) ?
Thank you in advance
Jack

---

### Post by Fafler on 2011-01-06
Man, i used to have a P2B-D board. It was really powerful back in the day. The biggest drawback is that you are capped off at 1 gb memory.

Your choices for 2D and really basic 3D: An older Geforce, Radeon or preferably Matrox card, like the G200.

The the absolutely best option is a Geforce 8400 PCI, but i don't think they are easy to come by anymore.

Ubuntu should run okay, but if you experience any problems, you should try out Lubuntu. Same basic distribution, but it uses a lighter window manager instead.

---

### Post by jack griffin on 2011-01-06
>>Man, i used to have a P2B-D board. It was really powerful back in the day. 

I just _love_ these sheet-sized things :)

>>The biggest drawback is that you are capped off at 1 gb memory.

Yes, that's true - it's going to be harder and harder to find a system that is happy with 
1 gb - still , my first pc was a p133 with 16 mb and entry level machines came with 8 mb !

>>Your choices for 2D and really basic 3D: An older Geforce, Radeon or preferably Matrox card, like the G200.
>>The the absolutely best option is a Geforce 8400 PCI, but i don't think they are easy to come by anymore.

I'll try eBay and see what I can find

>>Ubuntu should run okay, but if you experience any problems, you should try out >>Lubuntu. Same basic distribution, but it uses a lighter window manager instead.

Thanks for your fast reply
Cheers

---

### Post by gordintoronto on 2011-01-06
+1 to Lubuntu.

There are 59 PCI video cards (starting at $33) listed on Newegg, so the technology is not dead yet. I would stick with ATI/AMD or nVidia. I had good success with a card I bought for $10 on eBay. It has to use the generic drivers, but that's fine for what you want to do.

---

### Post by gregb49 on 2011-01-07
> **jack griffin said:**
> The motherboard is an elder (but fully functional) Asus P2B-D2 with dual Pentium III a 750 Mhz , 1 gb ram and integrated scsi support 8)... should I install a less resource hungry distro (like CrunchBang or Antix) ?If you haven't tried puppy linux it might fit your purposes better than Ubuntu (if I dare say that here) as it copes well with 750MHz boards, old graphics cards and even with only 128MB RAM, plus the hard drive install is minimal.

---

### Post by cascade9 on 2011-01-07
Puppy? On dual 750s with 1GB? Why oh why would you do that? 

I dont think that full ubuntu would run that well with that hardware. Going to lubuntu.....OK, if you like Lxde. I wouldnt, but I dont like Lxde. 

> **Fafler said:**
> Man, i used to have a P2B-D board. It was really powerful back in the day. The biggest drawback is that you are capped off at 1 gb memory.

Your choices for 2D and really basic 3D: An older Geforce, Radeon or preferably Matrox card, like the G200.

The the absolutely best option is a Geforce 8400 PCI, but i don't think they are easy to come by anymore.


Matrox......long time no see. 

They were always great cards, its a real pity that matrox dropped of the map. I guess that after Parhelia they felt that they couldnt keep up with nVidia and ATI. 

The only problem with the matrox cards is that they only go to 1280x1024 in digital (though they will run up to 2048x1536 with analog). 

I'd actually pick a matrox over a 8400GS for this system. Who needs 3D performance on a machine for websurfing and amule?

---

### Post by jack griffin on 2011-01-07
for gregb49 :
I'm sure Puppy will work well .I understand that it runs on Pentiums and 486s .
Too minimal for my taste, though .
I'd like to use Firefox or Iceweasel , don't think Puppy uses them .

for cascade9 :
Never tried Lxde .
Tried Fluxbuntu , liked fluxbox very much , but it looks like Fluxbuntu is dead :
last version was 7.10 .
I found CrunchBang , that uses openbox , very similar to fluxbox at a first glance .
BTW, if you don't like Lxde, which distro would you use on this machine ?

A new pci Matrox costs a lot (at least here in Italy) : a matrox qdi (128 mb) starts at € 572 ($ 749,32)
and even a Matrox Millennium G450 PCI (32 MB) starts at € 107 ($ 140,17) : 
that's definitely too much money
for my budget ! Even used ones are not cheap .

So far , I've got these options (on eBay):

PCI PNY VGA Graphics Video Card GF2MX20032SPCI 32 mb... € 19.57  $ 25,64
ATI RADEON 7000 PCI 64 MB Dual VGA....................................€ 34.97  $ 45,81
Sapphire Radeon 9250 128M PCI ATI Radeon.........................€ 40.24  $ 52,71
ATI Radeon 9200 128MB PCI Scheda video TV-Out VGA DVI...€ 40.95  $ 53,64
ATI Radeon 9000 scheda PCI video 3D DVI 256MB 256 MB.....€ 40.98  $ 53,68

What do you think ?

---

### Post by gregb49 on 2011-01-07
> **jack griffin said:**
> for gregb49 :
I'm sure Puppy will work well .I understand that it runs on Pentiums and 486s .
Too minimal for my taste, though .
I'd like to use Firefox or Iceweasel , don't think Puppy uses them .I use firefox, chrome (not always stable) and seamonkey with puppy. I just like the speed on low spec computers, ease of use and the features, although it has some quirks.

---

### Post by Firezap on 2011-01-07
Puppy works great on my older machine. I think I have lucid pup on it. Google Chrome and Firefox were just a click away if I remember right. It even came with Flash player that was ready to stream if I am not mistaken. Puppy has came a long way.

I would suggest trying to get a Nvidia card. It has always seemed easy to get the drivers I need for it. I looked on Newegg to and they had a cheap 30 dollar Pci Nividia card. It even had 256 megabytes of ram, so you could even do some 3d stuff with it. I bet Compiz would work fine.

---

### Post by dandnsmith on 2011-01-08
I've a PC, built from bits, in Spain.
Mobo - and old beast TMC TI6VG4
800 MHz CPU
768MB RAM (all that I could lay hands on compatible)
ATI Radeon 9200 PCI card (from Ebay)
LG display 1152x864

Runs UB 9.10, and UB10.04

OK for my purposes, while not very exciting.

---

### Post by cascade9 on 2011-01-08
I checked, I thought that the S3 Trio 64V2/DX went higher than 800x600. It does 1024x768 @ 85Hz (64k colours), 1280x1024 @ 85Hz (256k colours) and 1600x1200 @ 60Hz (256 colours). 

[http://docs.google.com/viewer?a=v&q=cache:Nn6HW6nv8FkJ:ftp://ftp.spez.com.ua/driver/viddrv/s3/s3_trio/po32tv2.pdf+S3+Trio64V2/DX+max+resolution&hl=en&pid=bl&srcid=ADGEESiRFsMeEMx_uGZ-ImwQ_sfpveqXYgi-cqCnSpVaHcAgHQBNeNgrUx1a4v7CNRSMp2n-yQkQ05KfCPIqYDARLNFZ7SQatyKWsKCthM7jVbwrTqjCimxD8ozK7-P_zPywSNZZbxGn&sig=AHIEtbQG3FTy_yBXFJ_JOsYVmouSFNLT2w](http://docs.google.com/viewer?a=v&q=cache:Nn6HW6nv8FkJ:ftp://ftp.spez.com.ua/driver/viddrv/s3/s3_trio/po32tv2.pdf+S3+Trio64V2/DX+max+resolution&hl=en&pid=bl&srcid=ADGEESiRFsMeEMx_uGZ-ImwQ_sfpveqXYgi-cqCnSpVaHcAgHQBNeNgrUx1a4v7CNRSMp2n-yQkQ05KfCPIqYDARLNFZ7SQatyKWsKCthM7jVbwrTqjCimxD8ozK7-P_zPywSNZZbxGn&sig=AHIEtbQG3FTy_yBXFJ_JOsYVmouSFNLT2w)

If you can deal with 64k or 256 colour display, 1024x768 or 1280x1024 should be do-able with the S3.  

> **jack griffin said:**
> for cascade9 :
Never tried Lxde .
Tried Fluxbuntu , liked fluxbox very much , but it looks like Fluxbuntu is dead :
last version was 7.10 .
I found CrunchBang , that uses openbox , very similar to fluxbox at a first glance .
BTW, if you don't like Lxde, which distro would you use on this machine ?

Fluxbuntu is gone, but fluxbox is still avaible with ubuntu- 

[http://packages.ubuntu.com/maverick/fluxbox](http://packages.ubuntu.com/maverick/fluxbox)

If it was my machine, I'm probably load up debian xfce. Debian gnome would run nicely as well, but I also dont like gnome (arent I picky?). Or I'd sell it and buy a newer computer, there are always people who will pay more for old servers than they are worth.  

> **jack griffin said:**
> A new pci Matrox costs a lot (at least here in Italy) : a matrox qdi (128 mb) starts at &#8364; 572 ($ 749,32)
and even a Matrox Millennium G450 PCI (32 MB) starts at &#8364; 107 ($ 140,17) : 
that's definitely too much money
for my budget ! Even used ones are not cheap .

So far , I've got these options (on eBay):

PCI PNY VGA Graphics Video Card GF2MX20032SPCI 32 mb... &#8364; 19.57  $ 25,64
ATI RADEON 7000 PCI 64 MB Dual VGA....................................&#8364; 34.97  $ 45,81
Sapphire Radeon 9250 128M PCI ATI Radeon.........................&#8364; 40.24  $ 52,71
ATI Radeon 9200 128MB PCI Scheda video TV-Out VGA DVI...&#8364; 40.95  $ 53,64
ATI Radeon 9000 scheda PCI video 3D DVI 256MB 256 MB.....&#8364; 40.98  $ 53,68

What do you think ?

Matrox cards were always expensive (thats what you get when you inist on high quality parts and manufacturing). I wouldnt buy one at those prices. 

The ATI cards cant use the ATI drivers (open soruce drivers only on newer ubuntu versions). ATI are better with open soruce drivers than nvidia in general from what I've experienced and seen. Those cards are overpriced though. 

GF2MX200 can use the nvidia drivers, but you'll need to manually install them (there is 96.xx drivers in the repos, for 10.10 but they dont work last I heard). Who knows when (if?) ubuntu will move to the next version of xorg and break the older 96.xx drivers. 

Pick your poison.....

---

### Post by Fafler on 2011-01-08
You should be able to locate old Matrox cards at fleamarkets and second hand stores. Look for (in order of speed, lowest to fastest) Mystique and Milllenium with 4 or 8 mb, G100, G200 or the G400. From the outside they can be recognized by the 15 pin connector next to the VGA. Gxxx cards in general have 
one or two blue VGA connectors. Cards with only one have it towards the top. DVI is rare.

---

### Post by jack griffin on 2011-01-09
> **cascade9 said:**
> I checked, I thought that the S3 Trio 64V2/DX went higher than 800x600. It does 1024x768 @ 85Hz (64k colours), 1280x1024 @ 85Hz (256k colours) and 1600x1200 @ 60Hz (256 colours). 

If you can deal with 64k or 256 colour display, 1024x768 or 1280x1024 should be do-able with the S3. 

This is actually an S3 Trio64V+ (2 mb ram, I found) , but the resolution is similar :
1280 x 1024 x 256 colours @ 75 Hz
1024 x  768 x 64k colours @ 75 Hz
 800 x  600 x 16.7M colours @ 75 Hz
(no 1600 x 1200 for this card)
(BTW, thanks for the link - it was useful)

I became more mad than I already was (and , boy, that's _hard_ :)) to get 1024 x 768 on screen, but at last I succeeded !
At 800 x 600 it was a pain in the *** : it couldn't even display a full window .
I surfed the web almost all day to get it done , found lots of howtos that didn't work ,
then wrote a new /etc/X11/xorg.conf file from scratch , bit by bit , until it worked !
I bid on an ATI R9250 128 Mb pci card on eBay, but it's good to have a proper resolution right now.

Downloaded Lubuntu and  tried it . I agree with you : Lxde is far from beeing cool .

So far, the box has dual PIII @ 450 Mhz (will be replaced by dual 750s soon) and 768 Mb ram (I checked and discovered that a 256 mb stick was faulty) .
Why, it works .

---

### Post by cascade9 on 2011-01-09
The link helped? Cool :) 

S3 made a right mess out of the Trio/Verge names. I've normally got a good memory for part numbers, but S3 video card names are just plain confusing.

---

### Post by Scot_Bernard on 2011-10-10
I'm configuring the same card (S3 Trio64V2/DX) with what seems to be 1MB Ram. With default installation settings I seen half of screen on the top, and bottom half in black. Got all screen being displayed using creating an xorg.conf with the following ( based on [S3 manual page]("http://www.x.org/archive/X11R7.5/doc/man/man4/s3.4.html") ):

    Section "Screen"

        DefaultFbBpp 24
        DefaultDepth 24
        ... 

    EndSection 

Because else 32bpp where selected by default. But max resolution available now is 640x480!


Can you please submit your working xorg.conf so I give a try?

Thank you!
> **jack griffin said:**
> 
then wrote a new /etc/X11/xorg.conf file from scratch , bit by bit , until it worked !


---

