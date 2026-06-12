---
title: "synaptics driver from SuSE to ubuntu"
date: 2011-06-18
forum: Hardware
---

### Post by J4K4 on 2011-06-18
I have **HP ProBook 4720s** and I have synaptics driver for SuSE Linux enterprise desktop.
I installed ubuntu 11.04 and I have touchpad driver problems (right click not working and other little problems)
this **synaptic touchpad driver** works fine on** suse/opensuse linux**.
I want to know if I can convert this driver to work on ubuntu too.
I tried extracting this driver and then when I executed I got error that there wasn't **libdbus-1.so** file...

---

### Post by J4K4 on 2011-06-18
[ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar](ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar)

here is the driver...

---

### Post by varunrajan on 2011-06-22
> **J4K4 said:**
> [ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar](ftp://ftp.hp.com/pub/softpaq/sp52501-53000/sp52904.tar)

here is the driver...

This link gives a rpm package. I tried to convert it to deb using alien but failed. Can someone who knows how to manually convert between rpm and deb please make the conversion?

Thanks

---

### Post by kaminem64 on 2011-07-12
this file is for i386, if you have a amd64 ubuntu then alien can't convert it to a amd64 deb file

---

### Post by cbennett926 on 2011-08-01
Where do you extract it to?

---

### Post by aldis on 2011-12-14
Hej Stygge och Välkommen [IMG]http://ubuntu.se/images/smilies/smile.png[/IMG]
Jag har själv ingen skrivare just nu och sist jag hade så var det med Vista, men hade exakt samma strul som du har nu [IMG]http://ubuntu.se/images/smilies/tongue.png[/IMG]
Hursomhelst, har du varit inne i Synaptic Pakethanteraren och slagit in  Brother i snabbsök? Det kommer upp några inläggsprogram som man ska ha,  står det.
Sedan undrar jag varför du har 9.10? Den håller på att fasas ut.

---

