---
title: "compaq presario hibernate/suspend fixed!"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by 4KvRMU7Nnv on 2007-08-26
I have a compaq R3000 series laptop with a nvidia geforce 64mb go card in it.  I discovered the reason it wouldn't wake up from hibernation or suspension was becuase it was trying to preheat the video card.  This can be turned off in /etc/default/acpi-support

change:

POST_VIDEO=true

to

POST_VIDEO=false

then try out suspend and hibernate and see if they work

---

