---
title: "Ubuntu 12.10+ on Gateway MD2614U"
date: 2013-06-20
forum: Hardware
---

### Post by Kelvari on 2013-06-20
I have a Gateway MD2614U that I have running Ubuntu 12.04 LTS. I know that, eventually, Ubuntu 12.04 will run out of support, but I also know that the AMD driver won't work on the newer kernels that come with Ubuntu 12.10+. Will I have to resign this laptop to a life with Windows once Ubuntu 12.04 expires to keep any semblance of performance? Or should I use the repsitory that rolls the system back to what's compatible with the AMD driver instead and just pray that I don't have any further trouble as a result?

Attached is my hardware profile, for anyone interested (ignore the bluetooth device, though).

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by Yellow Pasque on 2013-06-21
You have AMD graphics (not nvidia).
> product: RS780M/RS780MN [Mobility Radeon HD 3200 Graphics

The open-source radeon driver should work fine, especially by 2017.

---

### Post by Kelvari on 2013-06-21
I've found the performance - at least running off of a flash drive - to be far from stellar compared to even an old Intel graphics chipset with 12.10 and 13.04 from a flash drive. Should I go ahead and take the plunge for a full install on 13.04, then?

---

