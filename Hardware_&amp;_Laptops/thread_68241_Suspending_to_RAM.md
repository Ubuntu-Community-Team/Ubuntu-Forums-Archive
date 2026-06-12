---
title: "Suspending to RAM?"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by robfindlay on 2005-09-22
When I hit the logout button i get a "log out, shut down, restart, and a hibernate" 

The hibernate writes everything to the HDD and then shuts off, since hibernate is still sorta flakey --the network interface doesn't always come back up etc and I only have to drive from work to home about 10 min, i would like to just "suspend" the system to ram like i can under windows. 

Is "suspend" supported under ubuntu ?



Rob

---

### Post by fdimmling on 2005-09-22
Suspend to RAM is supported in Hoary but is said to work only for a minority of notebooks and is therefore disabled by default.
To enable it you have to uncomment the line 

ACPI_SLEEP=true

in /etc/default/acpi-support.

Friedrich

---

