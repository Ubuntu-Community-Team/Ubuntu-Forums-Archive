---
title: "Edgy SD Card reader recommendations"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by Pathogenix on 2006-12-31
Can anyone recommend me a card reader that'll auto-detect/auto-mount under 6.10?

SD Card support is a must, I'm not hugely bothered about any other format, though MMC would be useful.

Cheers,

 -- Flinky Wisty Pomm

---

### Post by 900i on 2007-01-01
Hi, I use a PNY 5in1 PCMCIA flash card adapter, part No PCMCIA51-NG.  Auto mounts cards when they are inserted.  Works flawlessly, is permanently inserted into laptop slot.

---

### Post by Pathogenix on 2007-01-01
Excellent, PCMIA wasn't something I'd considered but it might just work. Has anyone got a recommendation for a USB device? It'll be used on a laptop, but quite probably on a desktop first.

---

### Post by lswb on 2007-01-02
IME most any USB card reader works OK. I have a no-name I use quite frequently with SD cards ranging from 32MB to 2 GB and have never had anissue with it. I purchased it from an ebay seller some time ago, it was pretty cheap as I recall. Looking at it right now, I see no company or brand name on it. It just says

   "SD?Mini SD/MMC/RS-MMC/T-FLASH
                                Card Reader/Writer"

I have another older USB reader that I haven't used as extensively, but never had any problems with it either, and also a thumb drive adapter, that uses an SD card. All of these are automatically recognized and mounted on insertion (Using Dapper anyway) with an icon placed on the desktop.

I wish I could say the same for PCMCIA card readers. I don't like the USB reader sticking out of the back of my laptop and would like to have a PCMCIA card I could just leave in the socket. I tried a "6-in-one" card and it works with some SD cards, not with others. The problem is not just because of the size of the SD cards, either, as it works OK with some sizes of one brand card, but not with another brand of the same size. To make it worse, when it does fail, there's a kernel oops and often a system lockup. All these SD cards work fine with the USB reader, though. On top of all that, you have to edit some udev rules to get it to automount.

I may try the PNY PCMCIA card a previous poster mentioned and see how that works, I would like to be able to just leave an SD card reader in one of the PC card slots.

---

### Post by jblebrun on 2007-01-02
> **lswb said:**
> IME most any USB card reader works OK. I have a no-name I use quite frequently with SD cards ranging from 32MB to 2 GB and have never had anissue with it. I purchased it from an ebay seller some time ago, it was pretty cheap as I recall. Looking at it right now, I see no company or brand name on it. It just says

   "SD?Mini SD/MMC/RS-MMC/T-FLASH
                                Card Reader/Writer"

I have another older USB reader that I haven't used as extensively, but never had any problems with it either, and also a thumb drive adapter, that uses an SD card. All of these are automatically recognized and mounted on insertion (Using Dapper anyway) with an icon placed on the desktop.

I wish I could say the same for PCMCIA card readers. I don't like the USB reader sticking out of the back of my laptop and would like to have a PCMCIA card I could just leave in the socket. I tried a "6-in-one" card and it works with some SD cards, not with others. The problem is not just because of the size of the SD cards, either, as it works OK with some sizes of one brand card, but not with another brand of the same size. To make it worse, when it does fail, there's a kernel oops and often a system lockup. All these SD cards work fine with the USB reader, though. On top of all that, you have to edit some udev rules to get it to automount.

I may try the PNY PCMCIA card a previous poster mentioned and see how that works, I would like to be able to just leave an SD card reader in one of the PC card slots.

I'm also using a no-namer USB SD card reader by "ioConnect".... works flawlessly.

---

### Post by penguins-united on 2007-02-05
I think FireWire will autoplay on most systems too, and it's faster than USB -- great if you load from digicams, iPods, the like. Here's a useful [guide]("http://www.pickyguide.com/computers_and_software/sd_card_readers_guide.html") to SD card readers. :)

---

