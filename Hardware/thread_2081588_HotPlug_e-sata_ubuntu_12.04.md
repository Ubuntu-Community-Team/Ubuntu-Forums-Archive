---
title: "HotPlug e-sata ubuntu 12.04"
date: 2012-11-07
forum: Hardware
---

### Post by sdblepas on 2012-11-07
Hi all
I have a computer with Ubuntu 12.04 64B I also have a NAS 2 bay that can be connected via e-sata.
If I start my commputer with the NAS plugged in no problem but if I don't and plugg in the NAS afterward my drive are not mounted not even recognized with fdisk -l.
I searched a lot on google and saw some threads about it but nothing definitive.
Can you help?
Regards

---

### Post by sdblepas on 2012-11-11
up :)

---

### Post by pqwoerituytrueiwoq on 2012-11-11
is ahci enabled for your sata adapter in your bios?
if it is in ide mode that would explain it ide does not support hot plug but ahci does

---

### Post by sdblepas on 2012-11-11
Hi 
Tahnk you
Yes my ahci is defined in the Bios :( 
Regards

---

### Post by pqwoerituytrueiwoq on 2012-11-11
some boards have more that one sata controller are you sure your esata connects to a sata in ahci mode?

---

### Post by sdblepas on 2012-11-12
Nice catch pqwoerituytrueiwoq :)
I had 3 SATA controler :)
Thanks

---

