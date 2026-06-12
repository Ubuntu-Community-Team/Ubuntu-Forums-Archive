---
title: "NForce freezes my system?"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by storm3 on 2007-01-29
Hi,
i bought a new PC last week. AMD 64 X2 3800+, Gigabyte GA-M61PM with an NForce 430 chipset and socket AM2 and a SATA hdd. First i installed Ubuntu 6.10 32bit, but the NForce was not recognized and i had no network, audio and a display with fonts that can be decoded. I updated the Kernel to 2.6.19 and used the NVIDIA driver from their page. Now the chipset worked, but my system started to freeze every 15-30mins. I attached a picture of the freeze. I installed Fedora Core 6 and the chipset was running, but the system kept on freezing. I'm not shure if it is the NVIDIA driver that freezes, but with the NV i have no audio or useable fonts. Is there any solution?

---

### Post by DBG-LeNNy on 2007-02-04
My newly bought system has the same symptoms as yours. Also freezes every few hours of at least every night. It annoys me big-time.

My hardware is: Asus M2NPV-VM, X2 4200, 4 * 1Gb Asus QVL listed Corsair DDR2-800 memory.

I have little linux experience so my troubleshooting options are limited on this platform. The distro i have tried on this system are: (K)Ubuntu 6.06, 6.10, 7.04, Suse SLES10, OpenSuse 10.2.

On Suse my audio does not work properly and the system also freezes. On Ubuntu audio works with 6.06 and 7.04. All versions are AMD64 because i want to use the full 4Gb of RAM on my system.

After reading dozens of troubleshooting topics only one kernel parameter works around the problem. If i use the mem=4094 paramter all my problems are over on Ubuntu 6.06. But then i can only use 3.2Gb out of 4Gb installed RAM. So that is not an option for me.

The often mentioned parameter pci=nommconf has no influence on the stablility of the system.

If i can't solve this problem the next few days i return the board or run Windows 2003 R2 64-bit.

---

