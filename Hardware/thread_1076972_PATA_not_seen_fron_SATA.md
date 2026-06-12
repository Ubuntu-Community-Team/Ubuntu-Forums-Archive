---
title: "PATA not seen fron SATA"
date: 2009-02-21
forum: Hardware
---

### Post by andrew thompson on 2009-02-21
Hi

I am running UBUNTU 8.04 on a SATA drive with an ASUS M2N-MX SE PLUS motherboard. I also have a PATA drive.

My problem is that Ubuntu 'sees' the PATA but will not write to it.

Is this a BIOS problem or something more complex?

---

### Post by taurus on 2009-02-22
Do you mean "will not write to it" is due to permission problem?  What filesystem is that PATA and have you mounted it?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

