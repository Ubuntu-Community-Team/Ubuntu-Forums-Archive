---
title: "toshiba satellite A65 PnPBios problem"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by bcashman on 2005-07-12
I keep getting a pnpbios error when i am booting up. the system continues to boot,  but then i get 2 errors telling me that the pciehp and shpchp modules are not loading. The boot pauses here but then continues and appears to load normally. I guess this wouldn't be a problem but I am trying to get my wireless PCMCIA card to work, and I get errors in ndiswrapper saying the drivers i want to load are invalid and it wont let me modprobe ndiswrapper. This is probably not the best description, but im new to Linux. Any ideas?

---

### Post by varunus on 2005-07-12
The errors you are seeing are not fatal at all; they deal with loading pci-express hotplugging.  (Which shouldn't be necessary, unless you have pci-express cards that aren't video cards.)  What wireless card do you have?  Also, what is the output of lspci and lsmod?  Is it possible PCMCIA isn't being loaded correctly on bootup?

---

### Post by bcashman on 2005-07-13
thanks for the reply. Well, i tried to resolve the problem by loading 5.04. I dont get the messages anymore at bootup, but I am still having problems with ndiswrapper. outputs from lspci show 2 unknown devices, one of the wireless devices im trying is a d-link dwl 630 revA, but i have the same problem with lsusb which sees my netgear wg111. the problem is that ndiswrapper keeps telling me i have invalid drivers for both, but when i try -e it says they are not loaded. a -l shows them there as invalid drivers. Since im a noob this is getting frustrating. I have read all i can find with no luck.

---

### Post by bcashman on 2005-07-13
got the problem with the invalid drivers fixed, it was operator syntax error. I have yet to test it but at least the system sees the usp device and it blinks as it should. Still having problems with the PCMCIA card, the system doesnt see the card as ndiswrapper shows driver loaded, but no device present as the usb does. Still looking, and thanks for the help.

---

