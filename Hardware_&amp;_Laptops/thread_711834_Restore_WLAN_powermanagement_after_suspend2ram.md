---
title: "Restore WLAN powermanagement after suspend2ram?"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by schmolch on 2008-03-01
Hi,

i have to run a couple of things when the laptop resumes.
I reactivate my wacom stylus and usb-autosuspension via additinal files in /etc/acpi/resume.d/.
I tried the same with wlan-powermanagement but it seems that this attempt comes too early.

/etc/acpi/resume.d/99-power.sh
```
#!/bin/bash
iwpriv eth1 set_power 7
for i in `find /sys -name autosuspend -exec echo {} \` ; do echo "1" > $1 ; done
```

The usb-autosuspension gets re-enabled but the wlan power management stays off.

Anyone tried the same, any suggestions?

---

### Post by schmolch on 2008-03-05
bump

---

### Post by schmolch on 2008-03-11
Am i the only one using a Laptop here???

---

### Post by schmolch on 2008-03-16
Anyone answering will receive a free TCP/IP packet!

---

### Post by schmolch on 2008-03-19
bump

---

### Post by schmolch on 2008-03-20
bump!

---

