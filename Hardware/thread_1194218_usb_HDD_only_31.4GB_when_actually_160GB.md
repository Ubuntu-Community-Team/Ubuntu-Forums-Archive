---
title: "usb HDD only 31.4GB when actually 160GB"
date: 2009-06-22
forum: Hardware
---

### Post by rajanm1 on 2009-06-22
i had a spare 160GB IDE HDD lying around (its a samsung spinpoint sp1604n) so i bought an external usb enclosure for it and it works fine EXCEPT it is only reading as 31.4GB when it is a 160GB drive ?!? i have removed all of the "jumpers" on the back and tried in all sorts of positions but still no luck.  how can i fix this?

---

### Post by Eeqmcsq on 2009-06-22
What is the motherboard that you are reading this drive from? 160 - 31.4 is 128.6 GB, so my first guess is that you're motherboard uses 28-bit Logical Block Addressing, which has a limit of 128 GiB. 

Assuming this is correct, you'll have to check your motherboard to see if it supports 48-bit LBA, and see if there's a BIOS option and/or a BIOS update that enables 48-bit LBA. If your motherboard has absolutey no support for 48-bit LBA, you cannot safely use your 160GB on that computer.

---

### Post by rajanm1 on 2009-06-23
it is in a USB HDD enclosure so don't think it is problem with the mobo.
its is a msi 650i sli mobo anyway.

---

### Post by Eeqmcsq on 2009-06-23
Then I can only guess that the limitation is in the enclosure itself. What is the product number of your IDE to USB enclosure?

---

### Post by rajanm1 on 2009-06-23
problem resolved/solved :-) , all i had to do was to go to Control panel, administrative tools, computer management, storage, disk management and then delete the volume that is on it and it should show the whole thing as unallocated. Then create a new simple volume and tell it to use all the space.

---

