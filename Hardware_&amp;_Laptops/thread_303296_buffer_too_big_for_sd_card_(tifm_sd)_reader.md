---
title: "buffer too big for sd card (tifm_sd) reader?"
date: 2006-11-20
forum: Hardware &amp; Laptops
---

### Post by andree182 on 2006-11-20
Hi!

I'm using ubuntu for a few months now, but just yesterday I found out that in Edgy release something changed (maybe changing driver from sdhci to tifm_sd) and suddenly, my SD card 'reader' writes horribly slow on the SD card. It's not problem of the card or reader, as in Windows (or my mobile) it goes about 1.5 MB/s when writing sequential...

On the linux (kubuntu), when I copy something on the sd, it firstly goes as fast as 10-20 MB/s (obviously it's filling cache), but then the process gets stalled (with cache/memory full). I looked into /proc/meminfo - I suppose the 'dirty pages' means, how much there is left in the cache to be written. And the number decreased about 5kB/s! This doesn't, of course, happen with reading from the card...

Now - is the tifm_sd that slow, or the cacheing does completely kill the writing process? Is there any possibility to turn off cacheing for specific device? Is anybody here using the TI card reader in linux (ubuntu)?

PS: This is the reader:

06:07.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

---

### Post by zoly on 2006-11-21
Hi,
the same problem on ASUS A6JC-Q007 built in card reader which is:

04:01.2 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)

Any suggestion?

---

