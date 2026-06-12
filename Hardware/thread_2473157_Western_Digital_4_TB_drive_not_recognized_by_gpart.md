---
title: "Western Digital 4 TB drive not recognized by gparted on ubuntu 20.04"
date: 2022-03-25
forum: Hardware
---

### Post by rjbambery on 2022-03-25
I have a brand new out-of-the box Dell precision 5820 Tower with ubuntu  20.04 pre-installed on a 512 GB SSD.
It boots up properly.  
I added a 4 TB Western Digital Drive in slot next to SSD (WD40EFRX).
Installed gparted but it does not show the 4TB drive.
There is no Windows partition or windows software anywhere.

reseated, rebooted, power cycled, all the obvious stuff.
Searched for help but almost everything seems to involve
windows. (I do not have a windows machine).

Any help would be appreciated.

---

### Post by rsteinmetz70112 on 2022-03-25
What type of SSD?

---

### Post by rjbambery on 2022-03-25
M.2 512GB PCIe NVMe Class 40 Solid State Drive

---

### Post by oldfred on 2022-03-26
On some systems, a M.2 drive takes the place of one of the SATA ports. Or disables that SATA port.
Check your manual.

Does UEFI show drive in UEFI settings when installed?

---

### Post by rjbambery on 2022-03-26
Problem solved!
There are 4 slots in  Dell precision 5820 Tower 

SLOTS
-----------------                     ----------------
4TB                                   SSD
-----------------                    ------------------
-----------------                   -------------------
Empty                              Empty
-----------------                   -------------------

In this configuration the 4 TB disk was not recognized by Gparted.

SLOTS
-----------------                     ----------------
Empty                                  SSD
-----------------                    ------------------
-----------------                   -------------------
4 TB                                 Empty
-----------------                   -------------------

However, in this configuration
It was recognized and I was able to initialize it with gparted.

---

