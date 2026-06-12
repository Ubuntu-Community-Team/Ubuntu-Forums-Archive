---
title: "APC UPS via USB"
date: 2012-10-10
forum: Hardware
---

### Post by mike acker on 2012-10-10
should I connect my 12.04 Ubunbtu to my new APC UPS via the USB cable ?

any sudo apt-get needed after or before ?

---

### Post by ahallubuntu on 2012-10-10
When I plugged my APC UPS into a Ubuntu 10.04 LTS desktop via USB, it automatically detected it as a battery, like a laptop.  Unplug the UPS from the wall and it tracks the remaining battery life.  So, like a laptop, you can tell Ubuntu what to do as the battery drains: standby, shutdown, etc.  (You'd probably want it to shut down before the battery dies to protect your files, etc.)  I didn't have to install anything.

Try it on 12.04 - may work just as automatically for you as it did for me.

---

### Post by mike acker on 2012-10-12
worked like a charm :)

---

