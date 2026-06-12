---
title: "Atheros ar5007 works out-of-box"
date: 2008-09-21
forum: Hardware
---

### Post by highenergy on 2008-09-21
hi,

I have heard that atheros ar5007 wifi adapter doesn't work on ubuntu. Then I have a good news for you. Anyone who has atheros ar5007 wifi chipset should know that it works out-of-box in pardus 2008.1.

regards

---

### Post by phidia on 2008-09-21
> **highenergy said:**
> hi,

I have heard that atheros ar5007 wifi adapter doesn't work on ubuntu. Then I have a good news for you. Anyone who has atheros ar5007 wifi chipset should know that it works out-of-box in pardus 2008.1.

regards

Cool! This probably belongs in the community cafe though since it's not a request for help, but good to know.

---

### Post by IanW on 2008-09-21
This (ar5007eg variant on an EeePC701 in my case) also works out-of-the-box in Intrepid as of the move to kernel 2.6.27 due to the kernel now being built with Atheros' open-source ath5k & ath9k drivers.

---

### Post by highenergy on 2008-09-21
> **IanW said:**
> This (ar5007eg variant on an EeePC701 in my case) also works out-of-the-box in Intrepid as of the move to kernel 2.6.27 due to the kernel now being built with Atheros' open-source ath5k & ath9k drivers.

Hmm, good to hear that.

---

### Post by highenergy on 2008-09-22
well, I am trying xubuntu livecd 8.10 alpha6 now and I see that it doesn't support ar5007 chipset.

this is the error I got from dmesg output:
ath5k_py1: ......failed to wake up the MAC chip
ath5k_pci: ......probe of 0000:05:00.0 failed with error -5

---

