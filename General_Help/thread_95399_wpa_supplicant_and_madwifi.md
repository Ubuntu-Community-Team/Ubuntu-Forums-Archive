---
title: "wpa_supplicant and madwifi"
date: 2005-11-26
forum: General Help
---

### Post by Randy Sparks on 2005-11-26
I've got an Atheros-based PCI wifi card. 

I've followed the instructions in order to use wpa_supplicant with the card but have run into problems with the driver. 

The card uses code from the madwifi project but it appears that this has now been split into several separate modules. Mine is ath_pci, I think (I'm away from the machine at the moment). 

When I try and use this with wpa_supplicant I get told the driver isn't compatible. When I try and use the madwifi driver option, wpasupplicant appears to startup OK but the card clearly isn't connecting to the base station. 

The readme for wpasupplicant says something about compiling wpasupplicant with several options, but I don't want to compile from source unless I have to.

---

### Post by Randy Sparks on 2005-11-27
Sorry to be a pain but I'm sure somebody else will have come across this problem. Can anybody help?

---

