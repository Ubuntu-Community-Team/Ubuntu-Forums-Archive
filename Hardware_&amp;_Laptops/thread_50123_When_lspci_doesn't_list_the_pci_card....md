---
title: "When lspci doesn't list the pci card..."
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by Declan on 2005-07-19
So, I'm fairly convinced that my linksys wpc54gs wireless card won't work until lspci lists it.  If it is not listed, I believe that means it is not recognised.  Is that a fair assumption?
In which case, I may have a hardware difficulty?

The power light does light up, but nothing is listed in lspci for the card.
What might I try?

The laptop is a Toshiba A60-302.

Thanks,

Declan

---

### Post by pressureman on 2005-07-19
[QUOTE=Declan]So, I'm fairly convinced that my linksys wpc54gs wireless card won't work until lspci lists it.  If it is not listed, I believe that means it is not recognised.  Is that a fair assumption?
In which case, I may have a hardware difficulty?

The power light does light up, but nothing is listed in lspci for the card.
What might I try?[/QUOTE]

'lspci -vvx' is generally the next step to try when something doesn't appear. As far as I know, using 'lspci -x' should display all PCI devices, since it doesn't compare with the PCI IDs file - it essentially just dumps all the PCI device IDs that it sees on the bus.

From my experience, even unsupported hardware will at least identify itself to a 'lspci'. If it doesn't show up in that, it would seem that the card is not even reporting itself present to the system.

---

### Post by Declan on 2005-07-20
Thanks for that.  I've now more or less decided that I have a hardware difficulty.  Back for repairs again!  (this was not the only difficulty I was experiencing).

Merci bien,

Declan

---

