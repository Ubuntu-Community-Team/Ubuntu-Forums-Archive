---
title: "Newbie question:My Reboot and Halt not working on Laptop?"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by patrick295767 on 2005-10-24
Hi, 

I have a compaq 1685, pretty old pc .. .
with windows 2000, i could switch it off by clicking on Shutdown and also restart pc without any prob... 
But here, when i do reboot or shutdown -r now or halt ... the pc starts the init process and umount everthg, do everythg perfectly ... 
but hte last step : swiching that LED, i mean turning off the PC  gives no results : PC stays switched ON ...
  
Is there sthg to do ?
Could a genius help me to fix this ??

thank you very much

Best regards, 

Patrick

---

### Post by knappen on 2005-10-25
Try to add

acpi=off

to grub.

---

