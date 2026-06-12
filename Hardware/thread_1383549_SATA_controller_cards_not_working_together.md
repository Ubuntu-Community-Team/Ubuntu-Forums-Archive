---
title: "SATA controller cards not working together"
date: 2010-01-17
forum: Hardware
---

### Post by Aikon- on 2010-01-17
I am having a strange problem getting PCI SATA controller cards to work together. I would like three controllers to sit on the PCI bus together so that I can use up to six SATA drives.

Hardware:
  Motherboard: Abit NF7-S v2.0
  SATA chip A: Sil3112 (built into motherboard)
  SATA chip B: PDC20375 (add-on PCI, Promise SATA150 TX2Plus)
  SATA chip C: Sil3512 (add-on PCI, Bytecc)

My original configuration had only chips A and B, providing a total of four SATA ports, and worked fine for several years. Recently I received some new SATA drives and I would like to replace my aging IDE drives with these, however I required a minimum of 5 SATA ports, so I purchased the Bytecc board with chip C.

When both add-on cards are installed, none of my SATA ports work; when only one of them is installed (either B or C), all SATA ports work. All chips show up in `lspci`, however sometimes when both add-ons are installed, they are labelled incorrectly (even though their manufacturer and part codes, as shown with `-nn`, are correct).

I don't know where to go from here to get these cards working together; could someone at least point me in the direction I should be looking?

Please let me know if I can provide any more information that may help.

Regards,
-Aikon

---

### Post by Aikon- on 2010-01-24
Has no one any ideas?

I was playing around with BIOS settings trying to find something that would work (e.g. disabling serial and parallel ports to free up IRQs), but still to no avail. I found that I could disable the Sil3112A's "RAID ROM" and it would still work fine, so I tried installing the second card and yet again no joy. I also tried disabling the onboard controller from the BIOS entirely, but /still/ the same thing.

It would be superb if I could get this figured out, but I'm really at a loss for where I should be looking at this point.

-Aikon

---

### Post by IcarusR on 2010-01-24
Basic suggestion... have you tried them in different slots ? Away from each other ??
Could you not use fewer, bigger drives ? Thus only needing four ports & not both pci cards.

Sorry not very intelligent suggestions, but are just that.

---

### Post by Aikon- on 2010-02-10
> **IcarusR said:**
> Basic suggestion... have you tried them in different slots ? Away from each other ??
Could you not use fewer, bigger drives ? Thus only needing four ports & not both pci cards.

Sorry not very intelligent suggestions, but are just that.

I have tried them in every possible slot combination and did not find any difference.

I can't use bigger drives as these are SATA drives that I have on hand and am not really interested in spending any money this. I could use fewer drives and simply not use one of the 320GB drives, however this setup is not as good. If I can't get this card working, this is the route I will be taking.

-Aikon

---

### Post by cascade9 on 2010-02-10
Possibly some hardware conflict is stopping them from working. 

I know, you dotn want to spend any more money on this, but maybe this would be an idea-

[http://www.newegg.com/Product/Product.aspx?Item=N82E16815280003&cm_re=sata_pci-_-15-280-003-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16815280003&cm_re=sata_pci-_-15-280-003-_-Product)

4x SATA PCI card. Less than $25 US, shipped. Its got to be easier than sweating over the problems you're getting.

---

