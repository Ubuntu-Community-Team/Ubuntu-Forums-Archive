---
title: "Intel graphics card help"
date: 2010-07-13
forum: Hardware
---

### Post by blueysak on 2010-07-13
How do i install my intel graphics card so i can use compix?

---

### Post by AltomineUK on 2010-07-13
Intel graphics cards are often integrated (i.e. built in) with the motherboard, so installing new intel graphics card means installing new motherboard.

---

### Post by snowpine on 2010-07-13
You need to be more specific. Intel has many different graphics cards. If you aren't sure, use the terminal command 'lspci' (without the quotes).

Most Intel cards should be supported out-of-the-box without any special proprietary drivers or tweaks.

---

### Post by blueysak on 2010-07-13
> **snowpine said:**
> You need to be more specific. Intel has many different graphics cards. If you aren't sure, use the terminal command 'lspci' (without the quotes).

Most Intel cards should be supported out-of-the-box without any special proprietary drivers or tweaks.

The output is```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:06.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

```

---

### Post by snowpine on 2010-07-13
I am not familiar with 82845G personally, but a quick google search showed other users with the same question:

[http://ubuntuforums.org/showthread.php?t=1474759](http://ubuntuforums.org/showthread.php?t=1474759)
[http://ubuntuforums.org/showthread.php?t=1475474](http://ubuntuforums.org/showthread.php?t=1475474)

Hope that helps point you in the right direction, sorry I don't have any advice myself. :(

ps You do know that Compiz is optional software that is not necessary to use Ubuntu, right? All it does is make your windows wobble, sparkle, and spin. ;)

---

### Post by snowpine on 2010-07-13
Further Googling reveals your card is "blacklisted" by Compiz. No wobbly windows for you! :)

---

### Post by blueysak on 2010-07-13
> **snowpine said:**
> Further Googling reveals your card is "blacklisted" by Compiz. No wobbly windows for you! :)

so none of the effects will work?

---

### Post by snowpine on 2010-07-13
> **blueysak said:**
> so none of the effects will work?

See my previous post:

> I am not familiar with 82845G personally, but a quick google search...

I've told you everything I know, and suggest using the Search function at the top right of the screen, and/or Google, if you need more information. As far as I know, the Compiz blacklist is not easy to circumvent (nor would you necessarily want to do so). Good luck! :)

---

