---
title: "Hibernation and grub"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by sigmason on 2006-07-05
When I hibernate on my Dell Latitude C800, after pressing the power button to wake up the laptop, I get the grub loader.

Is there any way to get grub to select the kernel that was last loaded at that menu...or is there something wrong and am I not supposed to get the grub loader when resuming from hibernation?

sigmason

---

### Post by gborzi on 2006-07-05
I get the grub menu too after an hibernation. I think it's ok. I hibernated with a non-default kernel (386, my default is 686) but at the restart grub used used the default kernel, so that it went through a normal bootup.
I think it's possible to tweak the hibernate script in /etc/acpi to make the current kernel the default one.

EDIT: after reading grub info, I can say that tweaking the hibernate script is not needed. Change your /boot/grub/menu.lst as suggested here [http://www.gnu.org/software/grub/manual/html_node/savedefault.html](http://www.gnu.org/software/grub/manual/html_node/savedefault.html) .

---

### Post by sigmason on 2006-07-05
Much improved, that suggestion worked great.

Sorry I didn't catch that while RTFMing ;)

Also, thanks very much for confirming the behavior, it's always nice to know for sure then guess you're right :)

sigmason

---

