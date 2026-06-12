---
title: "Problem with acpi-button-lid: always closed"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by dany_r50 on 2007-07-02
Hello!

I have a problem with the **acpi **of my Samsung R50 laptop on Ubuntu Edgy Eft.
The problem is that when I obtain the following when I do:

dany@laptop:~$ sudo cat /proc/acpi/button/lid/LID0/state 
**state:      closed**

...And, as I am tiping on the laptop, **the lid isn't closed**.

¿How I could fix it?

¿It would be possible to write a script that forces to "open" the state of the lid on startup? (It could be possible that this way the system would be able to detect when closing).

Thank you in advance.

---

