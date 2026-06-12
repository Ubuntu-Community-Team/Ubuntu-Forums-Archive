---
title: "How do i install a network card"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by LukeWLL on 2006-10-31
Hey

I think this is a pretty silly question but ive just installed ubuntu 6.10 server on a dual nic machine and during the install i had to pick which was the primary nic, i did that but now i can only see one nic with ifconfig. how do i enable the second nic? its identical to the one thats working at the moment.

Thanks
Luke

---

### Post by deepwave on 2006-10-31
Run Networking Tools for the easy, graphical way.  Under the General select your Network device, click on Properties and check Enable this connection.

You can also manually configure the following:
/etc/networks/interfaces

---

### Post by LukeWLL on 2006-10-31
cause its server there is no graphical thing, editing the interfaces file worked tho, thanks:)

---

### Post by deepwave on 2006-10-31
Your welcome.

---

