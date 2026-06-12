---
title: "Linux won't read all RAM"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by swiftstealth on 2007-06-08
hey all, I have a tower PC that has 3 sticks of 256MB SDRAM on it, and linux only recognises the one stick of ram. I tested the sticks in different computers and they all work, and the bios of the computer detects it, but linux only sees 256. a little help?

---

### Post by coffeecat on 2007-06-08
How exactly is Linux only seeing 256 Mb? What app or utility are you using to detect the RAM? If you are using Ubuntu, open a terminal and type:

```
sudo top
```(or just 'top' from a root terminal in another distro) and post back what the 'Mem:' line reports.

---

### Post by Enverex on 2007-06-08
What motherboard and processor? I had/have this issue with an old 754 board with a 3000+ Sempron in it. The board just isn't compatible with the processor despite it claiming to be.

---

