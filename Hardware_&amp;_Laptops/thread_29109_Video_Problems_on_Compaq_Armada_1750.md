---
title: "Video Problems on Compaq Armada 1750"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by jivens on 2005-04-23
I hope someone has an idea. The install went well (as far as I can tell) and the laptop boots up, but when it gets to the point where you would login, the screen just goes white with some vague vertical stripes in the middle. Any ideas?

Thanks in advance.

---

### Post by 23meg on 2005-04-23
what kernel are you using? can you post the contents of your xorg.conf file?

---

### Post by jivens on 2005-04-23
[QUOTE=23meg]what kernel are you using? can you post the contents of your xorg.conf file?[/QUOTE]


Thanks for the fast response 23meg. I am using 2.6.10-5-386. However, during my blind meandering and exploring, I seem to have solved the problem. I simply removed the vga=771 expression from the boot string and this made everything aok (in case someone else has the same problem).:grin:

---

