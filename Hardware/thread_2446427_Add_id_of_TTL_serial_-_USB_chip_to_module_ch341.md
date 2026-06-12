---
title: "Add id of TTL serial - USB chip to module ch341"
date: 2020-06-30
forum: Hardware
---

### Post by christian02 on 2020-06-30
Hi All.
I'm using a TTL serial - USB chip, CH340K, which has a different id than the usual CH340G.
It works passing the new id via "echo 1a86 7522 > /sys/bus/usb-serial/drivers/ch341-uart/new_id" 
I'd like that the new id would be included in the module, so I tried to write to its maintainer but did not get a feedback.
I cannot submit a pull request on github because they are restricted to collaborators.
Any idea on what else can I do?

Thanks
C.

---

