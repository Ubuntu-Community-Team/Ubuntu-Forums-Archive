---
title: "Proper BIOS setting for PCI/IDE controller card..."
date: 2012-03-05
forum: Hardware
---

### Post by Moozillaaa on 2012-03-05
Anybody know the proper BIOS setting which makes drives on a PCI/IDE controller card show up as bootable devices?

My BIOS reverted to default settings, and now the drive attached to that card isn't showing in BIOS.

root@chucknb-desktop:~# dmidecode -s bios-version
080014

---

### Post by drdos2006 on 2012-03-05
Might be a hardware problem with the controller card. 

Turn the power off, removve power lead.
Open the case, remove and reinstall the card into the PCI slot, remove cables to the HDD and reattach. 

Dont forget to put your hand a metal part of the case before touching any electrostatically sensitive equipment.

regards

---

### Post by Moozillaaa on 2012-03-05
Thanks...

My battery went belly up, and needed replacement. Settings all reverted to default.

I don't remember which BIOS setting made the attached drive show up as a bootable device.

Anybody?

---

