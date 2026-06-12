---
title: "[How to] Fix the dark screen after suspend on thinkpad x61"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by lbharti on 2008-01-19
The screen that comes after a resume from suspend has a dark screen, and until now I had to switch between two terminals to get a backlit display. I was browsing through the /etc /default/acpi-support file and found out there was an option to enable that feature automatically. All one needs to do is to add/Enable this line 
DOUBLE_CONSOLE_SWITCH=true 
to the /etc/default/acpi-support file and that would be it.

---

### Post by johj on 2008-01-21
Yes! Thanks a lot for posting this! It works like a charm on my X61 :)

---

### Post by loko on 2008-04-23
Thx,

this also solved it for me.

---

