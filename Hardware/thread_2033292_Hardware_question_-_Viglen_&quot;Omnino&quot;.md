---
title: "Hardware question - Viglen &quot;Omnino&quot;"
date: 2012-07-25
forum: Hardware
---

### Post by nikonian on 2012-07-25
Hi.

Just bought this: [http://www.ebay.co.uk/itm/Viglen-omnino-17-All-in-One-Desktop-Computer-PC-Celeron-D-3-06GHz-1GB-80GB-DVD-/120955653369?pt=UK_Computing_DesktopPCs&hash=item1c2984ccf9#ht_1992wt_1185](http://www.ebay.co.uk/itm/Viglen-omnino-17-All-in-One-Desktop-Computer-PC-Celeron-D-3-06GHz-1GB-80GB-DVD-/120955653369?pt=UK_Computing_DesktopPCs&hash=item1c2984ccf9#ht_1992wt_1185)

Does anyone know if these will support Ubuntu 12.04? It has a Celeron D chip, but I've bought a Pentium D dual core to replace it. It has 1Gb DDr2, thanks :)


[EDIT]

Solved this now. The device uses a motherboard called a Viglen VIG580s, aka Asus P5LD2-VM/S.

My particular machine has both GMA950 *and* an Nvidia GeForce 6200, so after having turned off GMA950 in BIOS, I installed "nvidia-current" drivers. Next, in /etc/default/grub, ensure this line is present, as shown:

GRUB_GFXMODE=1024x768

Then save, and do "sudo update-grub" and reboot. This is because I had strange scrambled black text and black lines on white background, during boot & virtual console.

---

