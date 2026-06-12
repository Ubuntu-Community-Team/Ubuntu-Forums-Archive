---
title: "Ubuntu on a Toshiba Libretto?"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by jaykleg on 2005-06-01
Hi,

I realize that this thread might belong in the Laptop Support section, but please bear with me. I think that this is really not so much an issue caused by the fact that I am trying to use a laptop as the fact that I am using a system which has limited options for method of installation in circumstances where I have few network options.

The computer is a Toshiba Libretto L5W. This is a not-for-sale-in-the-U.S. notebook with no "legacy" ports. It has a couple of USB 1 ports, a PC Card slot, a very nice but odd 1280x600 screen, some sort of mongrelized ATi Radeon video subsystem, built-in wireless (802.11b), built-in 100 mbit Ethernet, a modem port, and no internal CD or floppy drive. I have a Panasonic KXL-830AN CD-ROM drive which connects to the system (and is powered through) a Panasonic "ATAPI CD-ROM Interface Card (JDWBL830AN).

The CD-ROM can be used to install Windows XP from a Norton Ghost image, but NOT from a retail / OEM CD because the install fails following the first reboot -- saying that it can't copy files. Likewise, an attempt to install Ubuntu 5.04 fails when it comes time for the setup routine to locate a CD-ROM drive.

There is a PXE-enabled LAN port, but I don't have a Linux server from which to load an image.

As far as I know these are the only common options for installing Ubuntu on a system of this type. I guess I could call Dynamism.com (where I bought the computer and CD drive in the first place) and beg them to sell me another of their expensive external CD drives, or maybe a floppy drive, to see if one of them will enable me to perform the installation. Frankly, they got enough of my money a couple of years ago for a computer which, while very nice for some very specific uses, was rather overpriced considering its level of functionality.

Do any of you know of an alternative installation method that might work with what I have on hand? I have a number of Windows XP Pro systems. Is it possible for me to host the network installation image on one of those? (I'm totally new to Linux. Lots of history with big iron and, more recently, with Windows.)

BTW, I have been [here](http://memebeam.org/toys/ToshibaLibretto) already. Otherwise, I would be even more ignorant than I am.

Someone strike me with a clue-by-four, please.

---

### Post by Jormundgand on 2005-06-01
Been reading the Jargon File?

I might suggest you try looking at the drivers Windows loads for the CD drive. It's obviously hideously nonstandard. It might also be worth contacting Toshiba for info.

I imagine it might be possible to use a USB linkage cable to mount the laptop as a partition on one of your XP Pro systems (I know from my sources boxes to mount the gap are available) and install on it from there (you might like to check out the guide available on installing Ubuntu without burning a CD).

Just throwing ideas into the cake. Hope that helps.

---

### Post by jaykleg on 2005-06-01
Yup, the drivers for the CD drive and its interface card are, indeed, non-standard. As a matter of fact they have been responsible for frequent blue screens over the life of the computer -- until I learned what combination of drivers and software were acceptable to the little unit. It has turned out to be a very nice system, but getting a fresh OS installation onto it is a challenge.

Over the two years I've owned the Libretto I have attempted communications many times with Dynamism.com, the people who sold the computer to me, and with Toshiba. Toshiba America has absolutely no information available on the system. It is my understanding that it was designed to be a Japan-only system. Japanese is beyond my ken, so contacting the parent company has been futile. There is no manual in English for the system.

Thank you for your suggestions. I'm unfamiliar with the concept of mounting the system as a slave drive via USB connection. Is there a particular term for that process -- a term that I might use in searching for information? I'm afraid that this system is such an oddball that I'm probably not going to find anyone with experience in doing this with the system.

The computer itself is nearly ideal for writing, having a keyboard which is of astonishing quality considering its size. It is unobtrusive in most settings, so it's also a good thing to take to meetings where it would be ridiculous to pop up a notebook with a 17 inch screen. I thought it might serve me as a good platform on which to learn about Linux. But I've got to get the OS installed first.

Thank you again for your help. Any further attempt at educating will be appreciated.

---

### Post by jaykleg on 2005-06-02
Okay, so my infatuation with slightly out-of-step hardware is biting me in the @ss.

I'm hoping someone is going to point me to a network installation guide, a how-to or how-tos which show me how to set up my network image on a WINDOWS machine (nothing else available), boot my little Libretto using a DOS boot CD (no floppy available) with PXE support, and install Ubuntu from the network image.

Really.

That's all I'm asking for.

I tried looking.

Honestly.

I also tried booting an Ubuntu Live CD on my other notebook. It happens to be from the opposite end of the laptop hardware spectrum -- a Dell Precision M70 with 2 gigs of RAM, a 2.13 GHz Centrino, and an NVidia Quadro FX Go 1400 (256 MB) video subsystem. Ubuntu won't work on that system, either. That problem is documented here on this forum as an issue with the NV driver included with the Ubuntu images. I could fix the installation on the Dell by doing a full installation instead of using the Live CD, but I have to maintain that computer as a Windows XP system for now because it's my main work system.

Do I really have to buy another computer to be able to install and use Ubuntu so that I can learn a little about it?

---

### Post by jaykleg on 2005-06-02
Found the guide on installing without a CD referred to earlier. I really don't want a dual boot system. I want a clean installation of Ubuntu on the Libretto, no other OS present. (The bloomin' drive is only 20 gigabytes, and I want to have some room for data.)

I'm looking to see if I can find a different external CD that will just let me do the installation. If I can't find that, I would still like to be able to just boot using the pre-install environment and get the image from a location on my network.

Am I being obtuse? I'm so busy these days it's hard to find time to focus on a project like this.

---

### Post by td5silver on 2005-06-22
Right now... the "2nd phase" of the installation is progressing on my Libretto L2 as I'm typing this on my WXP desktop.

To cut a long story short, I used a "surrogate" laptop (ACER Travelmate 800LCi) with built in CDROM to start the Ubuntu installation onto a 4.3GB HDD. After the selection of time zone, user name, blah blah... the installation prompts to remove the CDROM and restarts. At this point, I power down the ACER and removed the 4.3GB HDD.

I then transplanted the 4.3GB HDD into the Libretto L2. The L2 would continue with the installation. So far, I have 1 error with configuring fonts.

Will report back if the installation is successful...


And here is the l...o...n...g story:

I had been thinking of installing Ubuntu on a Libretto 110CT. But after reading thru a lot of forums, and getting nowhere, I decided to think out of the box. So, I came up with the above solution. However, after transplanting the 4.3GB HDD into the 110CT, installation freezes after 15 seconds, at some point about "kernel panic". So, I thought heck, why not try it on the L2, though I'm happy with WXP on it so far.

---

### Post by td5silver on 2005-06-22
Using my "surrogate" laptop and transplant HDD method, Ubuntu is up and running on my Libretto L2. I'm completely new to Linux (OS X is more my cup of tea), so I cannot say for certain Ubuntu is running perfectly.

So far, I'm able to surf the web (am typing this on L2 running Ubuntu and Firefox), and the power status looks correct (charging with 92% power etc).

---

### Post by jaykleg on 2005-06-22
I guess I should have posted back to my own thread. It just seemed that there wasn't any interest in it.

I got Ubuntu installed on the Libretto L5W by connect TWO external CD-ROM drives, the PC-Card-connected-and-powered Panasonic drive and a USB-connected Iomega Predator drive. The Panasonic drive was bootable but not supported natively under Ubuntu. The Iomega drive was not bootable but was supported natively under Ubuntu. So I performed the first part of the installation from the Panasonic drive, then switched the CD to the Iomega drive when the installation procedure asked for a CD-ROM drive. Dead easy.

Unfortunately the Linksys WPC54G wireless card I use in preference to the built-in 802.11b mini-card is not natively supported in Linux. I used ndiswrapper and the Windows XP driver for the card. That worked okay, but when I tried following the guide here for enabling WPA so that I could use AES encryption (a necessity for my purposes) I ran into nothing but stubborn snags. I could have continued working at it but decided to revert the system to Windows XP, for which it was obviously designed. I will reinstall Ubuntu on it when I find more information about the use of WPA with ndiswrapper OR when I finally decide to do it the easy way and purchase a natively supported wireless card.

In the meantime I will be using Ubuntu installed on a virtual machine or machines under Virtual PC 2004 running on the Dell M70 notebook, primary OS being WinXP. I figure this will enable me to really tinker with various installation configurations and with the OS itself while making it easy to get back to square one by simply copying the virtual machine's container file back into place over a borked installation.

---

