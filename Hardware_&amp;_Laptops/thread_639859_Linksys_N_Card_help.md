---
title: "Linksys N Card help"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by ShutItDown on 2007-12-13
im new here and i have been trying to get my Linksys N card to work for quit some time now. my mom wont buy me this new processor for my desktop till i get my laptop to work. any tips on how i can get it to work? ive searched the other wireless answers but i dont know exactly which steps to take. thank you.

---

### Post by lotacus on 2007-12-13
I don't know much about your problem, I too am having the same question, but with my intel wireless agn card. I hear that you can use ndiswrapper which enabled you to use the windows dll file within linux, that may help to get you connected to your wireless N network, however, though that my enable it at the driver level, the next bump would be to find linux software that provides wireless N support.

---

### Post by Dark_Stang on 2007-12-13
What type of card is it? If it's a pci card post the output of lspci, if it's a usb card post the output of lsusb.

---

### Post by ShutItDown on 2007-12-13
it goes in the side of my laptop. what info do you need? its not USB though.

---

### Post by Dark_Stang on 2007-12-13
Post the output of lspci for us.

---

### Post by ShutItDown on 2007-12-13
ian@Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
ian@Laptop:~$

---

### Post by Dark_Stang on 2007-12-13
The 4306 card is supported by default. Is there a reason you need the N card?

And... the linksys card isn't showing up there for some reason. What's the model number of it?

---

### Post by ShutItDown on 2007-12-13
we upgraded to the N router this September and that means i needed a N card so i bought it and worked fine with XP pro. I just cant connect to the internet now wireless.

Model # WPC300N

---

### Post by Dark_Stang on 2007-12-13
No no no no no, who told you that? Wireless G will work on an N network, you just won't get the speed and range out of it.

Edit: deleted all this

It looks like the card is broadcom based... everybody seems to be sharing a lot of parts these days.

Another edit: Now I get it... It's a BCM43XG with Linksys stickers on it.
And because of that... you should be able to use the wireless section I have in this thread [here...]("http://ubuntuforums.org/showthread.php?t=575750")

---

### Post by ShutItDown on 2007-12-13
you understand its a laptop right?

---

