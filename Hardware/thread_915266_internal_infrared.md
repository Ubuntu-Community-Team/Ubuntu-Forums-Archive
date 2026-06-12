---
title: "internal infrared"
date: 2008-09-09
forum: Hardware
---

### Post by wasutton3 on 2008-09-09
i have an asus m50sa-x1. i would like to get the internal infrared to work, but i have no clue how to do that. is there a way i could set it up so that i could at least test to make sure it would work?

---

### Post by DoctorMO on 2008-09-11
IR normally appears in /dev/ as a serial port, sending information to that serial port would allow IR communications. If it's not there then you may have to figure out in the Linux kernel in ubuntu supports your device.

---

### Post by wasutton3 on 2008-09-12
how would i tell which one it would be?

---

