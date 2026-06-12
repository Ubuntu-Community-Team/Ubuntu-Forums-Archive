---
title: "two different raid pcie controllers and can't access one of them through CLI"
date: 2020-03-24
forum: Hardware
---

### Post by alex346 on 2020-03-24
Hello,
I have Asus H97-PLUS motherboard and I have build it as NAS I have to use two different SAS/SATA raid cards:
[COLOR=#333333][FONT=&quot]ServeRAID M5014 SAS/SATA in PCI-e x4/x8 slot[/FONT][/COLOR]
ibm br10i - in PCI-e riser plugged into PCI-e x1


For me RAID functionality based on M5014 is OK, doesn't need more hardware raid, but that is not a problem now.
Both cards works together, even br10i in non-IT mode looks 'transparent' - so I can see drives through, part number, sn etc.
But as I rather need HBA I am thinking on changing it to IT-mode. I can do this if that is needed at this stage.

But - the main problem is - when I am trying to use storcli/storcli64 or megacli/megacli64 I cannot see the br10i adapter.
I have tried almost all possibility of that commands without success.
I see only M5014 card in all comands listed above.

**I would like to access also br10i raid controller ****from any cli command  **[B]to dynamically manage disks. - Is that possible when I am using both controllers?
[/B]


PS
To be honest - in PCI slot I have also Promise fasttrak tx3110 very old/vintage raid card - which is visible in coputer BIOS/POST.
And... all of 6 mb SATA ports I am using on MD raid devices.
But I suppose there is not a problem on bus, as the drives are visible and usable in ubuntu.


regards

---

