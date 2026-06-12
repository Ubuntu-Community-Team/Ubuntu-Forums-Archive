---
title: "[SOLVED] dual core noapic"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by Lacrimstein on 2008-04-11
I have recently purchased a Dell XPS M1530 laptop. Unfortunately, the driver for its Intel PRO 3945ABG Wireless card (iwl3945, i believe) had a bug in it that required the noapic kernel boot option. I have read that this option causes Ubuntu to recognize only one of the multicore processor's cores; However, I was surprised to see that with this option enabled, Ubuntu still recognizes both of my cores (and the wireless card works as well) Did I misunderstand something about noapic or is this a bug (although a welcomed one :) )?

My specs: Dell XPS M1530, 4GB RAM, 2.4GHz Intel Core 2 Duo, 256MB NVidia GeForce 8600GT

---

### Post by Ayuthia on 2008-04-11
> **Lacrimstein said:**
> I have recently purchased a Dell XPS M1530 laptop. Unfortunately, the driver for its Intel PRO 3945ABG Wireless card (iwl3945, i believe) had a bug in it that required the noapic kernel boot option. I have read that this option causes Ubuntu to recognize only one of the multicore processor's cores; However, I was surprised to see that with this option enabled, Ubuntu still recognizes both of my cores (and the wireless card works as well) Did I misunderstand something about noapic or is this a bug (although a welcomed one :) )?

My specs: Dell XPS M1530, 4GB RAM, 2.4GHz Intel Core 2 Duo, 256MB NVidia GeForce 8600GT

I think that the part that you are thinking about is actually nosmp.  That is usually causes linux to see it as one.  The main bug that lurks with the noapic (no Advanced Programmable Interrupt Controller?) is that it could cause some interrupt issues and turn off things like your USB ports.

---

### Post by Lacrimstein on 2008-04-11
Thanks for the reply!
Well, USB and everything else seems to be working fine for me, so no worries there :KS

---

