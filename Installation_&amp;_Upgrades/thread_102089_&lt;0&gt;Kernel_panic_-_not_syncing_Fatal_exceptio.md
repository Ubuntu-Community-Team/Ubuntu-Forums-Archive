---
title: "&lt;0&gt;Kernel panic - not syncing: Fatal exception in interupt"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by mangouste on 2005-12-11
Hello!

I've been trying to install Linux (Ubuntu then Mandriva seeing that Ubuntu couldn't install till the end) for 3 weeks now, and the installation keep stopping at the same point. Around 75% after rebooting and here is the message i get:
**<0>Kernel panic - not syncing: Fatal exception in interupt** :confused: 

- I checked both MD5 files for the files i downloaded through Ubuntu (& Mandriva) websites, and both were OK.
- I used 3 differents CD-ROM drives, still..
- I downloaded 6 times Ubuntu from different servers, still..
Same problem coming up, at the same time everytime.. :mad: 
- I try an installation on the other hard drive, still..

_My config:_
AMD 2100+
768 DDRAM
2 HD: 80GG & 15 GG
ATI Radeon 64MB
Creative 128
TrendNet Wifi card 128Mbits
Tekram SCSI card + Cdwriter Plextor
Network card (no cable plugged in it)

So After rebooting, Ubuntu is loading the modules, without syncronyzing because i didn't configure the network cuz of my WiFi card.
Then the rest of the installation continues with "Paquets installations" (in french...sorry.
I press CTRL+ALT+F4 for more description (going a little fast still....but...).

The last lines are long to type but it's something like:

Call Trace:
[<f08866cf>] pci_unmap_srb ....        *... = a lot of number and letters
                   srb_done ...
                   disconnect ...
                   dc395x_handle_interrupt ...
                   dc395x_interrupt
                   handle_IRQ_event ...
                   __do_IRQ ...
                   common_interrupt ...
                   acpi_processor_idle ...
                   acpi_processor_idle ...
                   cpu_idle ...
                   start_kernel
Code: 8b 54 24 04 8b 02 f6 .....
<0>Kernel panic - not syncing: Fatal exception in interupt

If someone has any ideas, i'll thank you!:razz:

PS: Installing Ubuntu Breezy Badger 5.10 from install CD

---

