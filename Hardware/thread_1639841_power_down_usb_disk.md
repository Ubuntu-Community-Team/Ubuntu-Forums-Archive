---
title: "power down usb disk"
date: 2010-12-07
forum: Hardware
---

### Post by surfer on 2010-12-07
i have a tiny server. parts of the operating system are installed on an integrated CF card (/boot and /) and the rest on an external usb disk (swap, /tmp, /var and /home).

when i hibernate the machine, the usb disk is not powered down. as it's a headless system, i can't tell when the shutdown is complete. but the external disk never spins down.

is there a way to power that disk down? i have seen it work on that system before...

---

### Post by surfer on 2010-12-07
...bump!

---

### Post by dandnsmith on 2010-12-07
There's a lot of suggestions from googling your post title.

One of the most interesting, which might tell you what you want is: [one site FAQ](http://www.nslu2-linux.org/wiki/FAQ/SpinDownUSBHarddisks)

HTH

---

### Post by viralmeme on 2010-12-07
> **surfer said:**
> when i hibernate the machine, the usb disk is not powered down

[Power off USB]("http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/")
--

[Dilbert on Dating]("http://www.dilbert.com/strips/comic/2008-05-21/")

---

### Post by surfer on 2010-12-07
thanks a lot! i'll try that tonight and report back.

---

### Post by surfer on 2010-12-14
hmmm... these suggestions seem to work when trying to power off a disk while the system is running. the hd i'd like to spin down contains vital mountpoints of the sytstem (/var, /tmp, swap). i would like to power the disk down when the system hibernates.

---

