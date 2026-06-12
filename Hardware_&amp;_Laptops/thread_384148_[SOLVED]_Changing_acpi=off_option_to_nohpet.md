---
title: "[SOLVED] Changing acpi=off option to nohpet"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by borobudur on 2007-03-14
To be able to install ubuntu on my machine I had to do it with this option
```
acpi=off
```now after installing I would like to change it to *nohpet. *

Where do I do this?

Thanks for your help!

---

### Post by borobudur on 2007-03-14
Found it!

After the installation with the acpi=off option, I had to edit the file **/boot/grub/menu.lst**. 

Here I found the **acpi=off **again and this I had to replace with [COLOR=SeaGreen]**nohpet**[COLOR=Black]. [/COLOR][/COLOR]
Now I can use all the battary functionality. Great!

---

