---
title: "suspend again???"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by rdunnam on 2006-11-17
Okay, so I got Beryl installed tested and removed... to much battery loss for my needs on this laptop.

Anyways, Prior to Beryl I had suspend working and then it stopped working, form what I read it was an ongoing issue.  Anyways it is off but suspend still does not work for me.  I have search this form and have googled it and I can not find out what is still stopping this from working.

Any insights will be very appreciated.

Rick

---

### Post by David Corrales on 2006-11-18
You probably switched to binary nvidia or ati drivers. If you want to suspend, use the open source **nv** or **ati** drivers.
This is a real problem for me, because in my laptop if I want to use the lower refresh rate modes provided by fglrx (to add 30 more minutes of battery) I can't suspend. If I want to suspend, I lose 30 minutes....

---

### Post by rdunnam on 2006-11-18
I had suspend working with the 'nvidia' driver before.
The settings on other forums had it working for me but after I reverted to non-xgl I can not reproduce the ability to suspend but I can not see what has changed as all those configs are still present.

Thanks,
Rick

---

### Post by David Corrales on 2006-11-18
Check to see which packages Beryl changed (for example libwnck, etc) and rollback them. If you're using dapper, you're in for a dependency problem ride.

---

