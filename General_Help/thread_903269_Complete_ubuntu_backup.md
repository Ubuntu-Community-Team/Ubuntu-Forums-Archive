---
title: "Complete ubuntu backup"
date: 2008-08-28
forum: General Help
---

### Post by david sousa on 2008-08-28
Is there a way of making a complete ubuntu back up? So that i can install it in another computer making it completely identical to the original...

---

### Post by Vivaldi Gloria on 2008-08-28
> **david sousa said:**
> Is there a way of making a complete ubuntu back up? So that i can install it in another computer making it completely identical to the original...

Take out the system disk from the ubuntu box and put it in another computer and ubuntu will just work on the new computer provided that:

1) Ubuntu uses a default kernel (you have not compiled a kernel yourself)
2) Ubuntu has no problem with the hardware of the second computer.

When ubuntu boots up it recognizes new hardware and adjusts accordingly.

So first try if the live cd works with the second computer. Now clone the ubundu disk (with e.g. clonezilla) to an empty disk and put it in the second computer. This will give you an exact copy of your ubuntu. Note that you may also need to partition the new disk with gparted first before you clone to it.

---

### Post by robert shearer on 2008-08-28
You could make a live cd/dvd of your existing installation.
This could then be used as an install disk in another computer.
It would be like installing from the original Ubuntu disc only with the programs, settings and updates you have chosen to use.

See these links for more..

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

[http://loscompanion.com/forums/index.php?topic=4249.0](http://loscompanion.com/forums/index.php?topic=4249.0)

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

---

### Post by david sousa on 2008-08-28
thanks

---

