---
title: "How to Check Hardware"
date: 2010-08-19
forum: Hardware
---

### Post by MacInAction on 2010-08-19
I suspect that my wireless adapter does not have the correct driver loaded. How are devices checked? I have an exclamation point in the wireless icon.

---

### Post by rdjse on 2010-08-19
The command 'lspci' can be used to view your hardware. 
To see a list of loaded modules(drivers) you can type 'lsmod'

---

### Post by MacInAction on 2010-08-19
I'm not familiar with Linux or command lines for that matter. Is there a way to manually locate and install a driver? What exactly does the exclamation point mean?

---

### Post by MacInAction on 2010-08-19
For those having minor hardware issues like mine, connect to the AP with a cable and update the system. After restarting, System>Administration>Hardware Drivers should now work (it did not before the system update).

I can only assume that the exclamation point in my original post meant that the driver was missing or wrong. It disappeared after the driver was installed.

---

