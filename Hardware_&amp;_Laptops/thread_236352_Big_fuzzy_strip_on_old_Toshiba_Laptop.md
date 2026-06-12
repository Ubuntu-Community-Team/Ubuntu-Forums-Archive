---
title: "Big fuzzy strip on old Toshiba Laptop"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by Rich43 on 2006-08-14
Hi,
I have a old Toshiba 4090CDS Laptop.. I am having problems with a severe band of random pixels near the buttom of the screen.

It was fine when it was used in windows but I need Linux on it. Any suggestions?

Heres a screenshot: [http://richieward.com/Screenshot.png](http://richieward.com/Screenshot.png)
Heres my XOrg.conf: [http://richieward.com/xorg.conf](http://richieward.com/xorg.conf)

PLEASE HELP!

---

### Post by foolsh on 2006-08-14
Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:0:4:0"
        Option "ShabowFB" "True"
EndSection

---

### Post by Rich43 on 2006-08-14
Thanks!

---

