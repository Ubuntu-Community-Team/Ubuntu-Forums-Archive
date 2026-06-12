---
title: "PCIe SATA nightmare - recommendations?"
date: 2018-08-10
forum: Hardware
---

### Post by boba23 on 2018-08-10
Hi guys,

I am really sick of playing around with my hdds, trying to get them to work reliably on a PCIe SATA controller. First of all here's my hardware config:

- Gigabyte B150M-D3H-CF
- Intel i3 6100T
- 16 GByte DDR4 RAM
- 6x6TB WD Blue WD60EZRZ
- 7x750GB Samsung Spinpoint F1 HD753LJ

I am running the 6x6TB WDs as software raid0 on the 6 onboard SATA Slots without any hickups, no problem what so ever.

The Samsung drives were the ones I used before I upgraded to the larger WD drives, now I wanted to use them as "backup" array for some stuff, yes I know raid is no backup, I am aware of that. So anyway, I wanted to run the Samsung drives as software raid5 on an PCIe SATA controller. Meanwhile I have 2 controllers here, which both have given me nothing but headaches:

- Highpoint RocketRaid 2720SGL (Marvel 94x Chip) - , uses "mvsas" kernel module. I am no using and don't want to the "hardware raid", just trying to use it as a dumb HBA/Controller for more SATA slots
- DeLock 89384 (AsMedia 106x Chipset), AHCI compatible, uses "ahci" kernel module

Anyway, I have been trying both (one at a time, not simultaneously)....results are:

- with both controllers, I get regular libata errors in the logs ending up in hard resets of the respective link and often downgrading speed to 1.5G.
- with the HighPoint controller I even get soft cpu lockups when returning my server from suspend (which is a must for me, I don't want it to run 24/7) resulting in a freeze of the whole system after a few minutes

I tried mostly everything .... new PSU (Corsair 750W), all new quality SATA cables, kernel parameters (noncq, pcie_aspm=off ... etc etc). Nothing seems to help.
In addition to getting those libata errors and hard resets the performance of the DeLock controller seems very poor, I get max 110MByte/sec when testing speed, though it's PCIe 2.0 x2 controller which should offer way more.

To narrow it down, I now pulled my WD drives, and put 6 of the Samsung drives (removed the spare) on the onboard controller. I have been writing to the array using "dd" for over an hour already without a single error in the log. I would have had tons already with the pcie controller. Plus, speedtest with hdparm gives me 370MByte/s for the array compared to about 100 with the onboard controller.

So my conclusion is, both of my PCIe controllers are crap, at lease for Linux usage.

What I would need is a 100% reliable and 100% ubuntu compatible HBA (no hardware raid needed) with at least 8 SATA ports and at least a PCIe 2.0 x2 interface that offers me 300MByte/sec plus read/write performance with my software raid 5 array .... is that asked too much?

I would really appreciate it a lot if someone could offer me some advice here on what controller to get, ah and btw, it shouldn't exceed the 250&#8364; price range if possible.

EDIT, ah forgot to mention I am running 18.04.1 Server 64bit

thank you,

boba

---

