---
title: "How to install drivers offline"
date: 2012-01-17
forum: Hardware
---

### Post by websterhamster on 2012-01-17
I have Lubuntu 11.04 installed on a Dell Inspiron 2500 (pretty old laptop). I am trying to get a wireless PCMCIA card that works in Windows to work on Lubuntu. I am pretty sure that the problem is that I don't have the right drivers installed.

Oh, I also don't have an Internet connection (can't get one until this card is installed :)

So, is there a way to install drivers without being connected to the internet?:confused:

Thanks for helping me!

---

### Post by searchfgold6789 on 2012-01-17
You can download them to a USB stick, burn them onto a CD, or procure a wireless USB card.
Though old hardware is usually supported. Look up documentation for the card to see if it should work out of the box, or if it only needs a bit of configuring.

---

### Post by MoreOrLess on 2012-01-17
It would be nice if you told us what wireless card you're trying to use.. ;)
Note: Extra credit for running lspci and telling us what chipset the card uses.

---

### Post by madvinegar on 2012-01-18
If you have the XP drivers of the card, you need to place them in a file and copy it somewhere on your computer (i.e. in downloads).

Then go through the "windows wireless drivers" and choose the file that ends in .inf

That should do it.

And just to get the extra credit:
I am using in one of my laptops a pcimci card as well (Netgear Wg511 v2) and I used the XP netgear drivers for the card (mrv8335.inf).:D

mike@mike:~$ lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83) 
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03) 
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) 
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03) 
mike@mike:~$

Is this the one?
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by websterhamster on 2012-01-21
Thanks for all the help! I actually have the drivers, I just need to know where to put them on the Lubuntu machine. The driver configuration program in Lubuntu won't let me manually choose a driver, so I guess I can just copy it into a folder somewhere. I just need to know the right folder.

Oh, and btw it's a Netgear WAG511 :)

---

### Post by websterhamster on 2012-01-21
WOAH!!

I just figured out why my card wasn't working, and I am so embarrassed! :oops: The network I was trying to connect to is a *N *wireless network, and the card I have is A/B/G!

<sigh> I think the card is actually working just fine, and I just didn't know it :)

Thanks for all the help!:D

---

