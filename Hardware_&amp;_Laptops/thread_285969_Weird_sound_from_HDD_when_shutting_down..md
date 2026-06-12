---
title: "Weird sound from HDD when shutting down."
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by julioromano on 2006-10-27
See this and also the duplicate bug linked there:
[https://launchpad.net/products/upstart/+bug/68614](https://launchpad.net/products/upstart/+bug/68614)

Every time I shut down Edgy Eft the hard drive makes a strange bad noise that is not present when shutting down Windows XP.

I think Edgy cuts the power too early (when hard drive is still reading).
There is no filesystem corruption (because fs is remounted read only before cutting power).
However the drive must perform emergency head park and this wears the drive faster than a clean spin down.
I think this behaviour occours only with SATA drives (I have another laptop with Edgy and IDE drive which does not have this problem).

Please let me know if you notice this behaviour.

Laptop model: HP Pavillion dv2172ea
HDD model: Seagate Momentus 5400.2 120GB SATA

---

### Post by zgornel on 2006-10-27
Interesting. I hear too sometimes some "strange clicks" on a Matshita 60GB SATA drive in both WXP and Edgy when shutting down. I think it's more a SATA controller flaw.

---

### Post by Potoni on 2006-10-27
Hi!! I have this problem too. I've already posted it but I got no answers: [http://ubuntuforums.org/showthread.php?t=284112]("http://ubuntuforums.org/showthread.php?t=284112")

My laptop is a Toshiba Satellite M50, with an IDE HD. I had no problems with Dapper, don't know what can be causing this...

---

### Post by julioromano on 2006-10-28
The correct bug is this:

[https://launchpad.net/distros/ubuntu/+source/acpi/+bug/68660](https://launchpad.net/distros/ubuntu/+source/acpi/+bug/68660)

I made a link to your previous post.

Bye
Marco

---

