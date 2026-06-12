---
title: "Hibernate PC"
date: 2008-09-04
forum: General Help
---

### Post by sv1cdn on 2008-09-04
Dear all.
Have made two installations of Ubuntu 8.04 One computer has an Intel motherboard and the other an ASUS one.
The one with ASUS hibernates fine but Intel it doesn't! After switching off from hibernate computer reboots from start.
Any idea on how to troubleshoot that?
Thanks!

---

### Post by jdemarco on 2008-09-04
I have an dell laptop with an intel chip that does the same thing. If it goes into hibernate, it will never come back up and I have to reboot. Any help with this would be greatly appreciated.

---

### Post by porchrat on 2008-09-04
I have a similar problem...Acer laptop can hibernate...desktop with a MSI motherboard can't.

I say screw it I never use hibernate anyway.

Seems to depend on your hardware and I believe it has something to do with how ACPI-compliant your hardware is.

Not much we can do except update the BIOS and/or kernel and keep your fingers crossed.

---

### Post by sv1cdn on 2008-09-05
Well, I found out that NVIDIA driver was causing this. Disabling this made hibernate work! I lost some 3D but I prefer to hibernate.
Before messing with NVIDIA I tried using uswsusp and s2disk, system seemed to go well into hibernate but couldn't resume (had to hard reset system).

---

### Post by Uchiha_madara on 2008-09-05
> **sv1cdn said:**
> Dear all.
Have made two installations of Ubuntu 8.04 One computer has an Intel motherboard and the other an ASUS one.
The one with ASUS hibernates fine but Intel it doesn't! After switching off from hibernate computer reboots from start.
Any idea on how to troubleshoot that?
Thanks!

i need to know how much space from your hard drive you allocated 
for Swap partition ?? and how much is the Ram ???


the swap partition should be larger in space more than Ram

for example ....if Memory is 512MB the swap partition should be 1G from the hard drive .....

I hope that is useful:):)

---

