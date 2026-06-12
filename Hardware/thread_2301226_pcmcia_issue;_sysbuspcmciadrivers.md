---
title: "pcmcia issue; /sys/bus/pcmcia/drivers/???"
date: 2015-10-31
forum: Hardware
---

### Post by bobmelville on 2015-10-31
I am trying to get a National Instruments GPIB PCMCIA-GPIB+ card going on a laptop under 14.04.
I have _almost_ everyting in place, but I believe I need an entry in

    /sys/bus/pcmcia/drivers

of the form
   ... /ni_pci_cs/new_id

a file into which I will put the vendor ID of the card I am trying to use.
Right now, the only thing in
    /sys/bus/pcmcia/drivers/
is a sub-directory (???) called

    (null)

I am unable to create either the needed sub-directory (ni_pci_cs) nor the file  new_id .
Even as root, I get a message that the file does not exist!!
Should I be able to, e.g.,  a mkdir ni_pci_cs
???
Any ideas would be much appreciated ...

Frustrated in NJ ...

---

