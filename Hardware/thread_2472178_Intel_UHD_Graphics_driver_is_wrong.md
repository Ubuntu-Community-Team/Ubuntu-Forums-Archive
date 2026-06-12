---
title: "Intel UHD Graphics driver is wrong"
date: 2022-02-20
forum: Hardware
---

### Post by miloskrsikapa on 2022-02-20
Hello everyone,
I have problems with various linux distros because my GPU driver is wrong. Intel N4020 have UHD 600 Graphics but when i type lspci I get this :
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 605 (rev 06)
Is there any way to change gpu driver to correct one?
Thanks in advance !

---

### Post by jeremy31 on 2022-02-20
It is using the correct driver, the UHD Graphics 605 doesn't matter as that info is obtained from a online database and doesn't affect what driver is loaded

---

### Post by Yellow Pasque on 2022-02-21
If you want to see the correct name, you probably just need to run "sudo update-pciids".
It looks like the 600 was incorrectly named in the database years after it first appeared, but should be fixed now: [https://pci-ids.ucw.cz/read/PC/8086/3185](https://pci-ids.ucw.cz/read/PC/8086/3185)

As jeremy31 points out though, that is just a human-readable string and it doesn't change what driver loads.

---

