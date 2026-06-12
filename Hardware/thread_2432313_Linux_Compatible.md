---
title: "Linux Compatible"
date: 2019-11-30
forum: Hardware
---

### Post by daniell59 on 2019-11-30
I am ready to order the parts for my new build. One question remains. Will it be Linux compatible?

MSI B450 TOMAHAWK MAX AM4 AMD B450 SATA 6Gb/s ATX AMD Motherboard 

AMD RYZEN 3 3200G 4-Core 3.6 GHz (4.0 GHz Max Boost) Socket AM4 65W YD3200C5FHBOX Desktop Processor 

Any insight into this will be greatly appreciated.

---

### Post by CatKiller on 2019-11-30
> **daniell59 said:**
> AMD RYZEN 3 3200G

AMD have struggled a bit to get support for their graphics hardware squared away before they release the hardware. My understanding is that the Ryzen 3000s were much less bumpy than the previous generation, but you're still going to be wanting to use the newest release rather than an older one so that you get a newer kernel and a newer Mesa stack.

---

### Post by daniell59 on 2019-11-30
If anybody can offer a better choice for a non gamer, I am open to suggestions.

---

### Post by CatKiller on 2019-11-30
It should be fine with the newer stack. [Here](https://www.phoronix.com/scan.php?page=article&item=amd-ryzen5-3400g&num=1) are some tests of that generation with 19.04, for example. It's just that having newer AMD graphics is the only time that I'd recommend going with the latest release rather than the latest LTS release.

The Ryzens make a really good platform.

---

### Post by daniell59 on 2019-11-30
Is there any rational  reason that i should step up to an X570 board?

---

### Post by CatKiller on 2019-11-30
Not really. PCIe 4.0 is the big draw, but there isn't really any hardware that can make use of it yet. They also all have support for the 3000 Ryzens, but so do the 400s that came after the 3000 Ryzens were released, and the ones that were out before then will support the newer processors with a BIOS upgrade.

---

### Post by Yellow Pasque on 2019-11-30
> **daniell59 said:**
> Is there any rational  reason that i should step up to an X570 board?

No, especially if you have no interest in OC'ing or high performance discreet GPU's. The X570 also has more SATA and USB ports, but you can always add those into a B450.
I was considering the X570, but the price difference from the 450 was too much and I refuse to buy any mobos with fans on the chipset (a lot of X570 boards have them because the chipset runs hotter).

I don't see any reason why the system wouldn't work with Ubuntu 18.04.3. It has fairl standard components (B450 chipset, Realtek 8111 LAN, Realtek ALC892 audio).

---

### Post by oldfred on 2019-11-30
AMD put out UEFI updates, that vendors then have to incorporate.

       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates in Aug as a "beta" though without explicitly acknowledging the Linux fix.

---

