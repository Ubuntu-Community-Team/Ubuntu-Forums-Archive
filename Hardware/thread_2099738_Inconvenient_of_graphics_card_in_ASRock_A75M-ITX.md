---
title: "Inconvenient of graphics card in ASRock A75M-ITX"
date: 2012-12-30
forum: Hardware
---

### Post by Alberto Slvador on 2012-12-30
Hi all!

A few days ago I bought a PC clone with the ASRock A75M-ITX, which included pre-installed Windows 7, not being a lover of that operating system, install Ubuntu 12.10 64 bits, everything was great, for not having a small problem with the integrated graphics card in said base plate and the corresponding drivers.

At the start of your PC, when running Ubuntu 12.10 64 bits, sometimes not displayed, the monitor appeared in the "No Signal", and perhaps should restart properly executed, also in turn have presented start the corresponding colored lines as indicating that something in the graphics card driver was not properly happening around me I decided to choose a proprietary controller thereby vanished completely implementing all the disadvantages, but when the start Ubuntu 12.10 64 bits, at no time could see more of the desktop wallpaper, Unity was not displayed, the top status bar and tools and/or others.

My last resort has been to expose this problem to all of you and with the intention that they can help solve the problems I'm having.

Happy New Year to all! :p

Greetings.

---

### Post by coffeecat on 2012-12-30
Welcome to the forum.

I'm using the micro-ATX version of that motherboard. They use the socket FM1 series of AMD CPUs, most of which have an integrated GPU as well, but you can get some FM1 processors with no GPU and with which you have to use a dedicated PCIe graphics card.

Do you know which CPU you have? Do you have a separate PCIe graphics card, and if so, do you know what it is? Do you get a display when you enter the BIOS? What are the BIOS settings for the graphics card?

Also - did you replace Windows with Ubuntu or did you set up a dual-boot such that you can still run Windows?

---

### Post by Alberto Slvador on 2012-12-30
> **coffeecat said:**
> Welcome to the forum.

I'm using the micro-ATX version of that motherboard. They use the socket FM1 series of AMD CPUs, most of which have an integrated GPU as well, but you can get some FM1 processors with no GPU and with which you have to use a dedicated PCIe graphics card.

Do you know which CPU you have? Do you have a separate PCIe graphics card, and if so, do you know what it is? Do you get a display when you enter the BIOS? What are the BIOS settings for the graphics card?

Also - did you replace Windows with Ubuntu or did you set up a dual-boot such that you can still run Windows?

Hello coffeecat!

First of all thank you for your interest, dedication and support to the downside I am currently having.

The processor is shown to me in the details is "AMD A4-3300 APU with Radeon (tm) HD Graphics × 2", can be displayed and you can access the BIOS settings, do not have the knowledge to know the configurations graphics card in them and use the integrated graphics on the motherboard.

Currently no hard disk is partitioned with any other operating system, counting only Ubuntu 12.10 64 bits.

Greetings.

---

### Post by coffeecat on 2012-12-31
Your A4-3300 APU has a dual-core CPU and a Radeon HD 6410D GPU. I am using the A6 3500 APU which has a triple-core CPU and a Radeon HD 6530D GPU - the GPU being the graphics chipset. Although I'm using a separate PCIe graphics card now, I did try the integrated graphics and if I remember correctly I had no problem with this with Ubuntu, and your 6410D ought to be able to work too. I will however check this later and post back.  

You weren't able to answer whether you have a separate PCIe card. We need to know this and if so which GPU your monitor is connected to. Have a look here:

[http://www.asrock.com/mb/overview.asp?Model=A75M-ITX#IOPhoto](http://www.asrock.com/mb/overview.asp?Model=A75M-ITX#IOPhoto)

Under the image of the motherboard itself are three small thumbnails. Click on the rightmost one which will give you a view of the rear connectors. You will see that the video connectors (VGA and HDMI) for the integrated graphics are positioned between the ethernet port and the audio sockets. If this is how your monitor is connected, then you are using the integrated graphics. If you have a PCIe card, there will be video sockets to the right of the audio sockets. Can you see such video sockets to the right of the audio sockets? If you can, you have a PCIe card.

---

### Post by Alberto Slvador on 2012-12-31
> **coffeecat said:**
> Your A4-3300 APU has a dual-core CPU and a Radeon HD 6410D GPU. I am using the A6 3500 APU which has a triple-core CPU and a Radeon HD 6530D GPU - the GPU being the graphics chipset. Although I'm using a separate PCIe graphics card now, I did try the integrated graphics and if I remember correctly I had no problem with this with Ubuntu, and your 6410D ought to be able to work too. I will however check this later and post back.  

You weren't able to answer whether you have a separate PCIe card. We need to know this and if so which GPU your monitor is connected to. Have a look here:

[http://www.asrock.com/mb/overview.asp?Model=A75M-ITX#IOPhoto](http://www.asrock.com/mb/overview.asp?Model=A75M-ITX#IOPhoto)

Under the image of the motherboard itself are three small thumbnails. Click on the rightmost one which will give you a view of the rear connectors. You will see that the video connectors (VGA and HDMI) for the integrated graphics are positioned between the ethernet port and the audio sockets. If this is how your monitor is connected, then you are using the integrated graphics. If you have a PCIe card, there will be video sockets to the right of the audio sockets. Can you see such video sockets to the right of the audio sockets? If you can, you have a PCIe card.

Hello coffeecat,

I use the two connectors, (VGA and HDMI) shown in this photograph.

[http://www.asrock.com/mb/photo/IO/A75M-ITX(m).jpg](http://www.asrock.com/mb/photo/IO/A75M-ITX(m).jpg)

Greetings.

---

### Post by coffeecat on 2012-12-31
> **Alberto Slvador said:**
> I use the two connectors, (VGA and HDMI) shown in this photograph.

Please confirm - not at the same time with one monitor.

I've done some experimenting on my system. Although the motherboard is the matx one, it has the same chipset as yours and almost certainly the same version of the UEFI-BIOS. Also, although my APU internal GPU is not the same as yours, it is in the same family and what works for me should work for you. I've confirmed the following:

[list][*]Ubuntu 12.10 works just fine with the onboard graphics and with the default open source driver. I see none of the problems that you do.
[*]With a PCIe card left in place, but with a monitor attached to the onboard graphics VGA port, and the BIOS set to PCIe for the graphics, I get no video signal at all.
[*]With the BIOS still set to PCIe for the graphics, but with the PCIe card physically removed, I get a signal from the onboard VGA port and can boot into Ubuntu and use it normally.[/list]

Based on the above, since you can view the BIOS, the BIOS settings should be OK, but I suggest you double-check them anyway. Switch on and at the Asrock splash screen, press F2 or DEL to enter the UEFI-BIOS setup screen. Now choose Advanced -> North Bridge Configuration. Under Primary Graphics Adapter, make sure it is set to "Onboard".

Re-reading your OP:

> At the start of your PC, when running Ubuntu 12.10 64 bits, sometimes not displayed, the monitor appeared in the "No Signal", and perhaps should restart properly executed, also in turn have presented start the corresponding colored lines as indicating that something in the graphics card driver was not properly happening around me I decided to choose a proprietary controller thereby vanished completely implementing all the disadvantages, but when the start Ubuntu 12.10 64 bits, at no time could see more of the desktop wallpaper, Unity was not displayed, the top status bar and tools and/or others.

I don't really follow that, but are you saying that sometimes you got no signal, but at others you did, and that because of this you installed the proprietary driver, and that after installing the proprietary driver it messed up the Unity desktop? Perhaps you could clarify the sequence of events. I do have to say that, unless you are interested in gaming, the proprietary driver is unnecessary. The default open source driver should be fine.

---

### Post by Alberto Slvador on 2013-01-01
> **coffeecat said:**
> Please confirm - not at the same time with one monitor.

I've done some experimenting on my system. Although the motherboard is the matx one, it has the same chipset as yours and almost certainly the same version of the UEFI-BIOS. Also, although my APU internal GPU is not the same as yours, it is in the same family and what works for me should work for you. I've confirmed the following:

[LIST]
[*]Ubuntu 12.10 works just fine with the onboard graphics and with the default open source driver. I see none of the problems that you do.
[*]With a PCIe card left in place, but with a monitor attached to the onboard graphics VGA port, and the BIOS set to PCIe for the graphics, I get no video signal at all.
[*]With the BIOS still set to PCIe for the graphics, but with the PCIe card physically removed, I get a signal from the onboard VGA port and can boot into Ubuntu and use it normally.
[/LIST]

Based on the above, since you can view the BIOS, the BIOS settings should be OK, but I suggest you double-check them anyway. Switch on and at the Asrock splash screen, press F2 or DEL to enter the UEFI-BIOS setup screen. Now choose Advanced -> North Bridge Configuration. Under Primary Graphics Adapter, make sure it is set to "Onboard".

Re-reading your OP:



I don't really follow that, but are you saying that sometimes you got no signal, but at others you did, and that because of this you installed the proprietary driver, and that after installing the proprietary driver it messed up the Unity desktop? Perhaps you could clarify the sequence of events. I do have to say that, unless you are interested in gaming, the proprietary driver is unnecessary. The default open source driver should be fine.

Hello coffeecat!

First of all I wish you all/as a happy new year, it said, procedeo to continue the conversation topic.

Regarding all that I've detailed in yesterday I check the BIOS settings, following your steps in option I indicabas, appeared "PCIe Express", to change the option to "Onboard", I was hope that everything could be solved, but it was not, I still have the same problems, to secure that now shows two symptoms, the earlier the "no Signal" and another, in which nothing appears just as if the image does not come properly.

With all this, I would, unless they occur more ideas and/or know which is likely if it can be by having both monitors connected and different outputs (HDMI and VGA), but I am surprised, but at this point, nothing be ruled out.

Greetings.

---

