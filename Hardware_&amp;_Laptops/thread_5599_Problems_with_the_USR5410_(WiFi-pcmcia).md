---
title: "Problems with the USR5410 (WiFi-pcmcia)"
date: 2004-11-20
forum: Hardware &amp; Laptops
---

### Post by Nerque on 2004-11-20
I try to use the ndiswrapper to install the windows drivers for USR5410 card, but I can't do it.

To install the drivers I have downloaded the drivers from USR page, exactly the 6.0b15 version (USR11G_v6.0b15.exe).

To extract the instalation files I have used the winzip. With this tool I have unziped the files data1.cab, data2.cab and data1.hdr.

With the I6COMP I have unzip the cab files and now I can use the usr11g.inf and usr11g.sys files.

I have copied the usrg11g files to an ubuntu partition. For example into the /tmp/wifi folder.

With this I have run the sudo ndiswrapper -i /tmp/wifi/usrg11.inf command.

Then sudo ndiswrapper -l. With this I can see the message usr11g hardware present.

Then sudo modprobe ndiswrapper.

In the system log I can't see the message "ndiswrapper: driver usrg11g added".

I don´t know how to continue.

What can I do?

Thanks.

---

