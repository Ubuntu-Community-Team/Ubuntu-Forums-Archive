---
title: "Zalman ZM-M401R not working at all."
date: 2014-02-09
forum: Hardware
---

### Post by dragonator2 on 2014-02-09
I bought a new mouse model ZM-M401R but it doesn't seem to work at all on Ubuntu. Works perfectly fine on Windows 7 x64. When booting in Ubuntu the lights on the mouse work but there is no movement or reaction from the mouse.    I could only find a couple of other instances online where something similar happened with a different model, but no solution.     Any suggestions would be appreciated.

---

### Post by alexander19 on 2014-02-14
I have a same problem :(

---

### Post by alexander19 on 2014-02-16
fix for this problem :D

include/linux/hid.h
[I]#define HID_MAX_USAGES [I]12288 
[/I]need to change from 12288 to 32768 and recompile kernel
[/I]

---

### Post by nadeem-orrie on 2014-11-29
I'm hesitant to recompile the kernel as i'm new to Ubuntu. Any good links on the topic?

---

