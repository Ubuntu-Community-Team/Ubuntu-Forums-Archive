---
title: "IBM/LSI SAS3444E controller not recognising 4TB drives"
date: 2013-06-15
forum: Hardware
---

### Post by MarcusL on 2013-06-15
UPDATE:
Bought Adaptec controller, and all is OK now.


Hi all,
I decided to upgrade a server box I built 2 years ago and have been running Ubuntu 11.04. The box contained 10x 2TB WD Greens in Raid 6. I decided to upgrade the server as a few of the greens started to die recently. I decided to go for WD Black 4TB drives to create my Raid 6 array. 

The new config is:

Asus P5K Deluxe mobo
Core 2 Quad processor (6x SATA Ports)
[COLOR=#000000]LSI manufactured, IBM branded, SAS3444E, 4x SATA Ports[/COLOR]
8GB RAM
10x WD Black 4TB HDDs

The problem I have run into is that the 6x HDDs on the mobo SATA ports are all seen as 4TB. When Installing Ubuntu, the partitioning step sees the drives as 4TB. The IBM/LSI SATA card sees the drives as 2.2TB, which is what shows in Ubuntu also.

I have tried finding a newer firmware but have not been successful. Here's details of the card and some of my findings:
[COLOR=#000000]
LSI manufactured, IBM branded, SAS3444E. Its FRU number (from a sticker on the card): 25R8071.

During post I can see the following on the screen: "SAS 1068E-IR 1.30.1.00 NV 2D:13".[/COLOR]

[COLOR=#000000]I had managed to flash this card 2 years ago when I first set up the server. The firmware gave me BIOS 6.30.00.00. [/COLOR]

[COLOR=#000000]I found the following firmware (BIOS 6.30.02.00.): [/COLOR][http://delivery04.dhe.ibm.com/sar/CM...dows_32-64.chg]("http://delivery04.dhe.ibm.com/sar/CMA/XSA/036o1/2/ibm_fw_mptsas_3g-sashba-2.75_windows_32-64.chg")[COLOR=#000000]. When I try and upload the firmware (via DOS bootable USB) I get the msg: "ERROR: The firmware Image is for a 106e b3 LSI SAS Controller, but the target adapter is a 106e b1 LSI SAS Controller."[/COLOR]

[COLOR=#000000]Sasflash -listall shows "LSI SAS 1068E(B1), FW: 01.30.10..00, NVDATA: 2d.13, x86-BIOS: 06.30.00.00, EFI-BSD: 03.16.00.06, PCI Addr: 00:04:00;00"[/COLOR]

I have never been able to access the LSI Config utility during post (Ctrl-C). The system tells me it will enter the config at the end of boot, then it does not, it goes straight into the OS.

My questions are:

1. Can the card be upgraded to support 4TB HDDs? I have not been successful in getting an answer to this, but sometimes its how you ask the question in the Google oracle of all knowledge!

2. [COLOR=#000000]If I cannot get the card flashed, what PCIe 4x Port SATA II controller can you recommend that is steady and stable and works well with Ubuntu? 
[/COLOR]
[COLOR=#000000]Thanks again for your help!

M
[/COLOR]

---

### Post by MarcusL on 2013-06-15
Update:

Following the steps in this post [http://hardforum.com/showthread.php?p=1038602393](http://hardforum.com/showthread.php?p=1038602393) I managed to flash the adapter to a std LSI FW & ROM, of a later date than what I had. I got the rom from here [http://www.lsi.com/channel/support/Pages/downloads.aspx?r=productfacet%3D%22AR8BTFNJIFNBUyAzMDgxRS1SOyBMU0kgU0FTMzA4MUUtUgxwcm9kdWN0ZmFjZXQBAl4iAiIk%22](http://www.lsi.com/channel/support/Pages/downloads.aspx?r=productfacet%3D%22AR8BTFNJIFNBUyAzMDgxRS1SOyBMU0kgU0FTMzA4MUUtUgxwcm9kdWN0ZmFjZXQBAl4iAiIk%22)

Sasflash now shows: [COLOR=#000000]LSI SAS 1068E(B1), FW: 01.33.10..00, NVDATA: 2d.03, x86-BIOS: 06.36.00.00, EFI-BSD: 03.16.00.06, PCI Addr: 00:04:00:00
[/COLOR]
Drives still seen as 2TB...

---

