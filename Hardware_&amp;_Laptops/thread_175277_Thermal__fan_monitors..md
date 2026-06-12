---
title: "Thermal / fan monitors."
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by sword- on 2006-05-13
Does anyone know any good applications to find out what your core temperatures and ambient temperatures are? I am currently using a Gigabyte board with the NVIDIA NForce 2 chipset.

---

### Post by Jason_25 on 2006-05-13
There are a few ways to do this.  The easiest way is to type
```

acpi -t

```
For your cpu temp.

For all other temps and fan speeds, you'll need to set up lm-sensors.  For that, see [this]("https://launchpad.net/distros/ubuntu/+bug/39407") page.

---

### Post by sword- on 2006-05-13
sword@ubuntu:~$ acpi -t
No support for device type: thermal

---

### Post by Jason_25 on 2006-05-13
Well you'll be doing it the lm-sensors way then it seems.  As for Nforce2, I have an Abit NF-7s Rev.2 that works with that command.  As do my Nforce4 boards.

---

### Post by sword- on 2006-05-13
I cannot get any temperatures from ksensors (obviously lm-sensors and libsensors is installed) but I can get hdd temperatures, which are normal. 

I can't figure out why I ksensors can't collect the ambient and cpu temperatures though.

---

### Post by Jason_25 on 2006-05-13
What does 
```

sensors

```
show?

Maybe you can try the script for lm-sensors that tries to load some other modules besides i2c.  It's linked to in the first link I posted.

---

### Post by sword- on 2006-05-13
root@ubuntu:/opt/firefox# sensors
No sensors found!

---

