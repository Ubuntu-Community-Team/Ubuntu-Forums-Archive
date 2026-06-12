---
title: "Grub Error"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by denis1982 on 2007-05-04
Hi
I installed ubuntu linux on my acer travelmate 2400 series laptop. It was a dual boot system with XP pro. When I tried to log in to ubuntu however, my password was not recognised. So I logged on to XP and formatted the hard disks with ubuntu on them. Now when I try to reboot my pc, I get a grub eror 17.
Also before, I used to get a screen saying " press F2 to get to setup" but now I don't get it.
Could anyone help??

Denis

---

### Post by sudo_nym on 2007-05-04
> **denis1982 said:**
> Hi
I installed ubuntu linux on my acer travelmate 2400 series laptop. It was a dual boot system with XP pro. When I tried to log in to ubuntu however, my password was not recognised. So I logged on to XP and formatted the hard disks with ubuntu on them. Now when I try to reboot my pc, I get a grub eror 17.
Also before, I used to get a screen saying " press F2 to get to setup" but now I don't get it.
Could anyone help??

Denis

Well, when you formatted that partition, you probably deleted [most of] Grub in the process.  However, part of Grub is still installed in the Master Boot Record of your HD.  So what happens?  The MBR part loads, but can't find anything else to finish booting with.

I'd suggest you reinstall Ubuntu, and be very careful how you set the password.  Are you sure you typed it exactly as you had during installation?  No criticism there, I've made some silly mistakes like not noticing the caps-lock was on, while setting the password for some online service or other.

Anyway, I hope it's that simple to fix.



Good luck,

Patrick.

---

### Post by sudo_nym on 2007-05-04
Nothing further to add, just forgot to subscribe to this thread, and I do want to follow-up on this, if I can think of anything that will help.

---

