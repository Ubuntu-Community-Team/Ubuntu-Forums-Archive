---
title: "No Sound &amp; No Scrolling on Touchpad"
date: 2015-11-20
forum: Hardware
---

### Post by aem0512 on 2015-11-20
Finally got Ubuntu 15.10 installed on my new Asus F555U. It was a pain to figure out (for me anyway). I had to put pci=nomsi in the grub config file to get it to boot up.

Anyway, at first after installing my sound worked fine but now I have no sound from the internal speakers or from the headphone jack. The sound works fine on the Windows side.

Also, how can I enable two-finger scrolling for my touchpad? I don't see that as an option listed in mouse & touchpad settings.

Thanks!

---

### Post by aem0512 on 2015-11-21
For the ASUS F555U, I decided to install kernel 4.3 since it is supposed to have the intel skylake support. I now have my sound back and a two finger scrolling option. 

I still needed to set pci=nomsi in the grub config to avoid booting into a screen full of garbled error messages "pcie bus error: severity=corrected type=physical layer". Hopefully within the next few kernel updates, that'll get fixed...

Hopefully this well help anyone else having the same issues.

---

