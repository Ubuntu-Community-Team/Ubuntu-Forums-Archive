---
title: "Laptop Overheating Solution"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by Sethro on 2006-08-09
I myself and alot of many other member have had the problem after installing Ubuntu was that either the fan was constantly at full speed or never on at all. After playing around with alot of setting and alot of configurations, I finally was able to make my laptop quiet down from full fan blast to low blast...

What will you need :

1. ) Boot Up Manager : Automatix user will find the applications in the automatix menu.

When Boot Up Manager is up and running you will find the following entry :

**"Controls CPU Speed And Voltage To Save Power"** -  Make sure this is enabled and fully functional.

2. ) Turn off and disable any other startup entry that deals with "Power" or "CPU".

The following feature was disable and I had alot of other power saving entries enabled. By making this change my laptop now wispers.

I hope this guide helped you guys out...

Cheers..

---

### Post by hopstah on 2006-08-09
have you had your laptop overheating to the point of shutting off suddenly?  and do you think that this would help with something like that?

---

### Post by Sethro on 2006-08-09
Well no the problem that I had was that I had was that my laptop was fan was constantly on at full speed. But I thing this will help people with the overheating problem..

---

### Post by gesho on 2006-08-09
you might want to be a bit more carefull with turning fans down, a lot of people are reporting laptops damaged by overheating.

if temperature is reasonable with lower fans - fine, but if it shoots up...

here is long thread on this:
[http://www.ubuntuforums.org/showthread.php?t=186003](http://www.ubuntuforums.org/showthread.php?t=186003)

---

### Post by caravela on 2006-08-10
what i don't understand is why there is a script to handle cpu scaling when there is modules on kernel that do that job, and are probabily better. Anyway for fan control you can try set it to allways on, via /proc/acpi/ .

---

