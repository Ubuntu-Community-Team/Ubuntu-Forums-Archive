---
title: "Adding video card. Listed in lspci but unable to use."
date: 2011-04-06
forum: Hardware
---

### Post by willburt on 2011-04-06
Hi,

I'm wondering if anyone has any ideas on this.

I have a dual head PCI-E card installed in my desktop (nvidia GTS 250). This works fine so I'm trying to add a third monitor with a nvidia geforce fx 5200.

After adding the video card and rebooting, the new card appears in lspci but ubuntu isn't recognising it.

I've tried editing the xorg.conf file to add the extra card and monitor but without success. I've also tried switching the BIOS to use the PCI card instead of the PCI-E which results in Ubuntu starting but without the xserver GUI.

I'm using the latest nvidia drivers.

I've attached my current lspci output and xorg.conf files in case anyone can help.

I'm at a loss as to where to go next; any help is much appreciated.

---

