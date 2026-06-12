---
title: "Flash memory won't work"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by aldav on 2007-12-07
I have this flash memory that worked. Two days ago a friend of mine took the memory and found a virus in it. He decided to format it. Since then, my memory won´t work. Windows XP recognizes it as a "Security Device" (which of course, it's not) and ask for drivers. In Ubuntu, when I connect it, no new devices appear on /dev by the name of sd*.
Any clues?
Thanks in advance.

---

### Post by PmDematagoda on 2007-12-07
Use Gparted to see if you can reformat the drive, it can be installed using:-

```
sudo apt-get install gparted
```

---

### Post by aldav on 2007-12-07
No, can't format the drive because I can't mount the flash. (because no new devices appear in /dev/ when I connect it, nothing happens. The memory LED flashes, but Ubuntu won't see it)

---

