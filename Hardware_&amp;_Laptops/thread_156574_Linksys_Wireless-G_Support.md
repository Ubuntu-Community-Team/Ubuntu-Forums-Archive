---
title: "Linksys Wireless-G Support"
date: 2006-04-07
forum: Hardware &amp; Laptops
---

### Post by Eltern on 2006-04-07
I'm thinking of installing Kubuntu on my parents' older laptop, which uses a Linksys wireless card to get on the net. I've read that these things have rather crummy support on Linux, because it uses a Broadcom chipset (which we don't have the specs on). However, the sources that I've read this on are about a year old now. Is it too much to hope that Breezy Badger has support for this card out of hte box? What about with minimal fuss?

The model number is WPC54GS.

Thanks for the help!

---

### Post by spd106 on 2006-04-07
Have a look [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards"), it suggests ndiswrapper for the moment. The bcm43xx driver may work with it, that should be included with dapper in june, afiak it will be merged into the kernel before too long. You could always try an alpha release to test it out if you're feeling impatient.

---

