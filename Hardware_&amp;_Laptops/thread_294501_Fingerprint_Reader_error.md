---
title: "Fingerprint Reader error"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by flammen on 2006-11-06
Ok, I'm pretty sure everything is installed that needs to be for the fingerprint reader in my Lenovo N100 to work.  I'm at the point where I'm trying to run ./Sample from the NonGUI_Sample folder in the TFMESS folder.  

I run Sample as root and get this...root@1[NonGUI_Sample]# Sample
Starting Sample Application
Major=1 Minor=10
BSP Index= 0
BSP Name: libbioapi_dummy100.so
Description: BioAPI v1.1 Dummy BSP
Vendor: Example Vendor
Module ID: {ffffffffffffffffffffffffffffffff}
Device ID: 0x00000000
BSP Index= 1
BSP Name: libpwbsp.so
Description: BioAPI Password BSP
Vendor: BioAPI Consortium
Module ID: {263a41e071eb11d49c34124037000000}
Device ID: 0x00000000
BSP Index= 2
BSP Name: libtfmessbsp.so
Description: TouchChip TFM/ESS Fingerprint BSP
Vendor: UPEK, Inc.
Module ID: {5550454b2054464d2f45535320425350}
Device ID: 0x00000000
Please enter your user id
kellen
Please enter your password for enrollment:

Please enter your password for verification:

MATCH!
Ending Sample Application

It never asks me to collect any fingerprints.  Anybody know why this is happening?

---

### Post by flammen on 2006-11-06
bump

---

