---
title: "Extremely Strange Wireless Problem"
date: 2008-05-31
forum: Hardware
---

### Post by RapidDemon on 2008-05-31
I own a Sony Vaio TXN25N/B which comes stock with an Intel IPW3945 wireless card.  The default drivers for this are iwl3945, which load and work just fine.  Recently my wireless card starting giving me trouble so I switched to a stock Atheros 5BXB6 that I had lying on the shelf.  Supposedly this uses the AR5006 chipset.  However, when I boot into Ubuntu wireless works fine, but it shows that the iwl3945 driver is loaded.  A quick lsmod and a look at dmesg confirms this.  Can anybody tell me what is going on here?  On one of the other operating systems I boot this could be a problem since the card appears to be misidentifying myself, even though under Ubuntu it seems to work fine.

---

### Post by attari on 2008-05-31
> **RapidDemon said:**
> I own a Sony Vaio TXN25N/B which comes stock with an Intel IPW3945 wireless card.  The default drivers for this are iwl3945, which load and work just fine.  Recently my wireless card starting giving me trouble so I switched to a stock Atheros 5BXB6 that I had lying on the shelf.  Supposedly this uses the AR5006 chipset.  However, when I boot into Ubuntu wireless works fine, but it shows that the iwl3945 driver is loaded.  A quick lsmod and a look at dmesg confirms this.  Can anybody tell me what is going on here?  On one of the other operating systems I boot this could be a problem since the card appears to be misidentifying myself, even though under Ubuntu it seems to work fine.

Atheros does not work well with Ubuntu. I too barely got it to work using ndiswrapper and WinXP drivers. My Atheros WiFi came with Acer laptop.

My advice is to only use hardware that is supported on Ubuntu else life is plain misery! :)

---

### Post by k33bz on 2008-06-05
> **RapidDemon said:**
> I own a Sony Vaio TXN25N/B which comes stock with an Intel IPW3945 wireless card.  The default drivers for this are iwl3945, which load and work just fine.  Recently my wireless card starting giving me trouble so I switched to a stock Atheros 5BXB6 that I had lying on the shelf.  Supposedly this uses the AR5006 chipset.  However, when I boot into Ubuntu wireless works fine, but it shows that the iwl3945 driver is loaded.  A quick lsmod and a look at dmesg confirms this.  Can anybody tell me what is going on here?  On one of the other operating systems I boot this could be a problem since the card appears to be misidentifying myself, even though under Ubuntu it seems to work fine.

I will suggest taking a look at my thread. It might do the job for you on that Atheros Wifi card.[http://ubuntuforums.org/showthread.php?t=800686&highlight=k33bz]("http://ubuntuforums.org/showthread.php?t=800686&highlight=k33bz")

---

