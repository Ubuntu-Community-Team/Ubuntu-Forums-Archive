---
title: "IBM T42 internal ethernet card"
date: 2008-08-26
forum: Hardware
---

### Post by Rysith on 2008-08-26
I'm trying to install Ubuntu 8.04 on an IBM T42 laptop, and I can't get it to acknowledge the existence of the integrated gigabit ethernet card. I know it's an Intel PRO 10/100/1000 adapter, but I can't see it on lspci, much less in something reasonable like ifconfig. All the searches that I've done have been about getting the wireless card to work (which claims to be working, although I don't have wireless where I am right now). Does anyone have suggestions for how to get the card detected? It seems like someone would have mentioned it if the Intel cards didn't work with Ubuntu.

---

### Post by Rysith on 2008-08-26
Just an update: The Intel Pro/1000 drivers do seem to be loading according to dmesg (at around 634, version 7.3.20), but the card does not appear in lspci. The card worked in Windows prior to installing Ubuntu, so I doubt that the card is dead. Is there any way to make Ubuntu strenuously probe for new devices?

---

