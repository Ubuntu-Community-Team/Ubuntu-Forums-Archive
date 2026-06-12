---
title: "Card reader fails to mount SDHC cards unless logged in as root?"
date: 2009-01-29
forum: Hardware
---

### Post by jarthurs on 2009-01-29
I have a Toshiba A100 laptop with a built in card reader (Texas Instruments PCIxx12), it works fine with SD cards up to 2Gb but has never worked properly with SDHC cards.

I was doing some research the other day just to see if the reader even supports SDHC and inserted a 4Gb card to see if I could find any reference to it in fdisk. To my surprise it mounted and I could read/write the card. I figured that something had updated and a fix had been applied relating to the card reader.

Later on I put the same 4Gb card in and 'nothing'... Puzzled I thought back to what had been open the first time and remembered I had just installed a package, hence I had used sudo. So I opened a terminal screen and fired off 'sudo fdisk -l',then reinserted the SDHC card and bingo it mounted 1st time.

As much as I don't use SDHC cards often, is there any way I can automate this process to allow high capacity cards to mount like normal SD cards?

Thanks,
Jason.

---

