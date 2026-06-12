---
title: "A possible solution to Power Management problem"
date: 2006-04-10
forum: Hardware &amp; Laptops
---

### Post by karthik085 on 2006-04-10
Someone posted on forums that Ubuntu was not properly supporting Power Management on their laptop. I could not find the thread by searching on the forums. 
Anyway, I found good info on this website, regarding acpi modules:
[http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/)

You should apt-get install acpid. You can configure it to do things whenever an event happens. For example, in the default configuration, a system shutdown is initiated whenever the power button is pressed. I load the following modules in /etc/modules:
# ACPI modules
thermal
processor
fan
battery
ac
button

I do not know if it is going to help the problem. But, it may be worth a try.

---

### Post by chele on 2006-04-13
That article is from Dec.2004 It may be a bit out of date by now.

---

