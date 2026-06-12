---
title: "Slow DVD drive with SATA connection on Laptop"
date: 2009-04-28
forum: Hardware
---

### Post by nicolasdiogo on 2009-04-28
hi folks,

i have this problem with laptop where my DVD-ram is very slow..

it is a T61p lenovo with a DVD (HL-DT-ST DVDRAM GSA-U10N) attached to a SATA which is seem as a SCSI disk.

i have tried some of the suggestion that i have found on this forum but it does seem to work.
for instance, i tried adding this to my kernel grub option in menu.lst

```

combined_mode=libata

```

and also added to /etc/modprobe.d/options

```

options libata atapi_enabled=1
options ide hdc=noprobe

```

The DVD is attach via a sata connection and BIOS is set with AHCI.

does anyone know how to improve performance with this setup?


i have attached the HARDINFO for this machine so you can see what is been loaded and used.

thanks a lot in advance for your time.

Nicolas

---

### Post by nicolasdiogo on 2009-04-29
Anybody?!

thanks,

---

