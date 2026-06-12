---
title: "vaio s260/memory stick"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by uncle vernon on 2005-08-28
hi, all -

i have hoary running on my sony vaio s260 laptop.  it has a built in memory stick slot that i'm trying to use.  i plug it in and nothing happens.

neither /var/log/syslog or /var/log/message registers anything.  i tried to modprobe the standard modules and:

uhci was not found
usb-uhci was not found
usb-ohci was not found

sd_mod and usb-storage loaded, but didn't make a difference.  i know that the logical step would be to recompile the kernel and build the other three modules, but i REALLY don't want to if i don't absolutely have to.  i'm using the stock kernel, which works great for everything else, but doesn't include the source (or the .config), so recompiling would be time consuming and a guaranteed pain in the ass.  does anyone have another idea?

thanks a lot,
casey

---

### Post by Corey on 2006-08-09
I have the same laptop and I am also stumped with the memory stick reader. Any progress?

---

