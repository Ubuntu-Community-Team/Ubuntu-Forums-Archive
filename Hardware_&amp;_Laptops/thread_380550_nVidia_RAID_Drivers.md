---
title: "nVidia RAID Drivers"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by ee99ee on 2007-03-09
I have a new dual AMD Optron server I'm trying to get ubuntu 6.10 loaded onto.

This is the server:
[http://www.supermicro.com/Aplus/system/1U/1021/AS-1021M-T2RV.cfm](http://www.supermicro.com/Aplus/system/1U/1021/AS-1021M-T2RV.cfm)

This is the motherboard:
[http://www.supermicro.com/Aplus/motherboard/Opteron2000/MCP55/H8DMR-i2.cfm](http://www.supermicro.com/Aplus/motherboard/Opteron2000/MCP55/H8DMR-i2.cfm)

This box is based on the nVidia nForce Pro chipset and has an onboard SATA2 RAID controller I'm trying to use. When I run the installer, I only see the four drives seperately even though I have gone into the RAID setup and configured the drives as a single RAID-5 array.

Apparently, the only offical drivers are for SuSe and RHEL and are only distributed in RPM format. Is there anyway I can ubuntu loaded with RAID support? I do not want to use software RAID.

Here are the drivers:
[ftp://ftp.supermicro.com/driver/SATA/nVidia/MCP55/Linux](ftp://ftp.supermicro.com/driver/SATA/nVidia/MCP55/Linux)

-chris

---

### Post by mgmiller on 2007-03-09
Actually, your onboard raid is still software or "fake raid".  To read more about it and see a list of true hardware raid cards, go to the link below.  With a properly supported, true hardware raid card, you won't need any drivers, and the raid will "just work".

[http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")

---

### Post by ee99ee on 2007-03-10
crap...thanks!

---

