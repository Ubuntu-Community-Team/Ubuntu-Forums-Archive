---
title: "EVGA GeForce GTX660 Problems"
date: 2013-10-14
forum: Hardware
---

### Post by will10 on 2013-10-14
I've very recently started using Ubuntu and everything is going good for the most part, except I cannot get my GPU (EVGA GeForce GTX660 version: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814130911](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130911)) to display any video, so I have my monitor plugged into my motherboard.  I've tried several different drivers and none of them seem to do anything.  Also, GRUB will only come up when the monitor is plugged into my GPU, which is the only way I can boot into windows as well.  Do I need to try an open source driver or is something wrong with my install?  Pretty much in the dark here.

---

### Post by Donut50 on 2013-10-15
Do you have an intel cpu or is there a intergrated graphics card on your motherboard?
Try to disable the intergrated graphics card in your bios.

---

### Post by will10 on 2013-10-15
> **Donut50 said:**
> Do you have an intel cpu or is there a intergrated graphics card on your motherboard?
Try to disable the intergrated graphics card in your bios.

Yes, it's an intel with intergrated grpahics, where would that be in the bios?

---

### Post by Donut50 on 2013-10-16
it is different with every motherboard because every manufactuer puts its own bios on the motherboard.
On my motherboard the path is: advanced settings, onboard devices configuration, onboard graphics controller.
I disabled it, maybe this works for you.

If that doesnt work try this: advanced settings, chipset, southbrigde configuration, and set primary graphics adapter to (pcie - pci - igp)

Igp is the onboard graphics, pcie is your graphics card.

---

