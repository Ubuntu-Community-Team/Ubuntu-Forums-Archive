---
title: "Any way to trick the OS hardware list?"
date: 2012-11-07
forum: Hardware
---

### Post by pakopako on 2012-11-07
Trying to figure out a workaround an old Toshiba hardware problem (the SD TypA Controller -- the internal SD card Reader) and I can't get my head around how the reader works under a Knoppix rescue CD (Hiren's BootCD), Anti-X, even Puppy Linux, but not Ubuntu 11.04.

The hardware shouldn't be too much different from the Ricoh SD card reader (which apparently has [noted](http://goinggnu.wordpress.com/2009/11/12/read-your-sd-card-with-your-ubuntu-laptop/) [workarounds](http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD_card_working) and in Windows, people can use [url=http://www.tabletpcbuzz.com/showthread.php?36590-M200-Windows-7-Drivers-amp-Issues]HP's CardBus drivers/[url] with no problem.

I've tried using NDISwrapper to load the HP drivers, but trying to install SFFdisk.INF causes NDISwrapper to hang (SDbus.INF works). Is there a more generic driver, or an ability to import whatever Knoppix found, or a manner to fool the OS to find a different hardware than what's actually there?

---

### Post by gordintoronto on 2012-11-07
Which Toshiba? With an SD card plugged in, what does lsusb display? (Or maybe lspci?)

NDISwrapper seems to be for wireless cards.

Before today, I've never heard of difficulties with a card reader. Perhaps the quick solution is to buy a cheap USB card reader? Where I live, they cost about $4.

A later version of Ubuntu might help. I think 11.04 has expired?

---

### Post by pakopako on 2012-11-09
Thanks for the reply gordintoronto.  This is a Toshiba M200 -- historically, this issue has pretty much stuck with it. 

LSPCI displays the same *Toshiba SD TypA Controller* that plagues other threads, [this one being the most recent]("http://ubuntuforums.org/showthread.php?t=1581734"). Ubuntu won't recognize anything in the SD slot. Even Windows needs an alternative driver (the HP cardbus based on Ricoh's chipset) to recognize most SD cards. Later versions of Ubuntu will be problematic on my old laptop. I tried a  12.04 liveCD and said my Intel Pentium-M processor lacks the PAE  instructions to run it.

While NDISwrapper was made for wireless cards, you can load other Windows drivers with it (likely to varying degrees of success), or at least that's what I figured. Hence why I also asked if drivers could be taken from other Linux distros. (Puppy and Knoppix live rescue CDs see the card slot, no problem.)

I do have  USB card readers, but it's become annoying as I only have 1-and-a-half USB slots on this machine and I don't want to have to rely on a powered USB hub to expand my slots.

On a related note, anyone know anything about how to trace leads on an M200 motherboard? The 2nd USB slot (the one farther from the AC adapter) provides ample power, but no data. I would think this wasn't by design. As far as I can tell, the USB port looks fine; all four pins are OK and nothing wobbles.

---

### Post by cwsnyder on 2012-11-09
NDIS wrapper takes Windows drivers for networking cards and converts the APIs to plug in to the networking API on Linux in the Linux kernel.

If you want to check the drivers in the Knoppix CD, type lsmod in a terminal.

Something else to check on SD cards: If your SD card is between 2G and 32G, it is a SDHC (SD High Capacity) card, not an SD card, and requires different firmware in the reader.  If it is more than 32G in size, that is ANOTHER upgrade in firmware to enable it to be used.  Check it out if you don't believe me.

---

### Post by pakopako on 2012-11-10
> **cwsnyder said:**
> If you want to check the drivers in the Knoppix CD, type lsmod in a terminal.
Huh, I totally forgot to do that. I'll reboot tonight and see if I can get a workaround.

> **cwsnyder said:**
> Something else to check on SD cards... SDHC... requires different firmware in the reader.  If it is more than 32G in size, that is ANOTHER upgrade in firmware to enable it to be used.
Totally believe you (Toshiba's Windows driver will not support SDHC cards and requires installing HP's RICOH driver), but "reader firmware?" Do you mean like a BIOS update, a kernel patch, or a driver file?

---

### Post by cwsnyder on 2012-11-10
No, actual update of the firmware in the hardware interface between the computer and the SD card.  It won't 'present' the proper form for the USB storage device connection without a firmware update.  And in most cases, that requires a hardware change, not something which is user update-able.

---

### Post by pakopako on 2012-11-10
Hmm. Well, in Windows the card reader can read/write to all my SD cards (512mb 1gb, 16gb, 32gb) so hopefully the reader firmware can support everything.

---

