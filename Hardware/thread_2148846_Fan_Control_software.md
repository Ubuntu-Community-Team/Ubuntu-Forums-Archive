---
title: "Fan Control software?"
date: 2013-05-26
forum: Hardware
---

### Post by blaz1ngra1n on 2013-05-26
I have recently installed Ubuntu 13.04 in EFI mode on my retina macbook pro.( Dual Boot with OS X) However, I cannot help but noticing that my CPU temps are completely abnormal (reaching 80 degrees with simple web browsing). This is probably due to some incompatibilities in the Apple Hardware. 

Can anyone recommend fan control software for ubuntu? Thanks.

---

### Post by Yellow Pasque on 2013-05-26
The fan is controlled through ACPI. Do you have a hybrid graphics system? That can heat up your system. Check output of:
```
lspci | grep VGA
```

---

### Post by blaz1ngra1n on 2013-06-08
Yes, I have the NVIDIA Discrete Card and the Intel HD Graphics card, although I believe the open source nvidia drivers are in use.

---

### Post by blaz1ngra1n on 2013-06-08
Here is the exact output:

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M Mac Edition] (rev a1)

---

