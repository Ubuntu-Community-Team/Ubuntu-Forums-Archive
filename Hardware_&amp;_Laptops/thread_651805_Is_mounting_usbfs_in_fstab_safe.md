---
title: "Is mounting usbfs in fstab safe?"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by ZDemon on 2007-12-28
Hi guys.

Just a quick question.

Is mounting usbfs in /etc/fstab with permission 0666 safe?

Thanks.

---

### Post by kidders on 2007-12-29
Not really...

In theory, that would allow anyone with access to your system to perform arbitrary operations on your USB devices.

---

### Post by ZDemon on 2008-01-03
So its OK? Hmm, i was afraid because of the permission level.

Thanks kidders.

---

### Post by kidders on 2008-01-03
No... I don't think it'd be a very good idea, tbh.

---

