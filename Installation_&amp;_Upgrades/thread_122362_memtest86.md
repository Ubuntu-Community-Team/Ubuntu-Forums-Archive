---
title: "memtest86"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by Klaidas on 2006-01-27
Hi, 
I have updated ubuntu. IUn the updates, there was a kernel image also. So I updated, and the default boot became memtest86. Anyway, I changed it back to Windoze by editing menu.lst 
So, what does the memtest86 do? There is an option in the menu.lst not to create a memtest boot option. Do you have it set to true, or false?

```
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true
```

---

### Post by JAwuku on 2006-01-27
The memtest86 is optional, it just does extensive read/write tests to the RAM, to check for any defective chips. I'm not sure what OS/kernel it's based upon.

---

