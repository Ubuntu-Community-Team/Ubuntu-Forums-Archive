---
title: "Sabrent wireless card not working - SOLVED"
date: 2013-07-04
forum: Hardware
---

### Post by rghpkp on 2013-07-04
Summary: A while ago, my Sabrent wireless-N pci adapter (PCI-802N) stopped working.  Long story short, the Sabrent card is not compatible with the new linux kernel (3.5).  Short of rolling back to the 2.6 kernel, there is no workaround.

Details: This card uses the Ralink RT2860 chipset.  The official drivers for this chipset were last updated in 2010, and designed for the linux kernel 2.4 (I think).  The drivers apparently worked through kernel version 2.6.

Ralink merged with MediaTek in January 2013, and the old RT2860 driver is still available for download in a .tgz.  A message through MediaTek's official contact form, asking about updating the drivers and continued linux support was not returned.  The "linux driver" link on Sabrent's page takes you to the same obsolete driver.

I contacted Tiger Direct about kernel 3.5-compatible wireless cards; after a short hold, I was told that they don't carry any at this time.  They've since removed the "Linux Compatible" tag from the PCI-802N product page.  The PCI-802G uses the same chipset, but is still labeled "linux compatible" at tiger direct.  

Can anybody recommend a PCI wireless card that is working with linux kernel 3.5 or higher?  Documentation showing driver compatibility would be great too.

---

