---
title: "Toshiba Qosmio F10 Install problem"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by pixil9 on 2005-06-23
Hey all,
I boot off the ubuntu cd and the install works perfectly until the reboot
It then says "Grub HD install error" or "Grub HD error" can't remember..
Anyone?
Thanks
Tyler

---

### Post by Skroob on 2005-06-23
[QUOTE=pixil9]Hey all,
I boot off the ubuntu cd and the install works perfectly until the reboot
It then says "Grub HD install error" or "Grub HD error" can't remember..
Anyone?
Thanks
Tyler[/QUOTE]
 That happend to me too.  I have a Qosmio F15.  Maybe not your ideal solution, but I used my Windows restore cd to put the Win boot loader  back on.  Then I configured it to boot into grub as well.

If you figure out how to triple boot (Linux, Win, QosmioPlayer) I'd be really interested.  The Qosmio Player is installed into unpartitioned space and I haven't been able to figure out how to get grub to boot it.  They are using LILO so it must be possible.

---

### Post by phantom on 2005-06-23
If they use lilo, then why make it harder ?  :???: 

Just run install lilo and it will pick up and configure all bootable partitions.

---

### Post by Skroob on 2005-06-26
Because they are booting to a nonexistant partition.  I looked around for a little bit but I haven't figured out how to do that in either LILO or GRUB.

---

