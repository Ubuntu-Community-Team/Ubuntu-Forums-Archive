---
title: "ul80vt - no intel graphics in lspci"
date: 2011-03-05
forum: Hardware
---

### Post by sonee on 2011-03-05
Hi everyone,
First I am sorry for my english because I am not a native english speaker :)
Currently I have an Asus UL80Vt and Im new to linux/ubuntu.
I'm having troubles with the graphics drivers.
My laptop has 2 graphics cards - 1 integrated and 1 discrete - nvidia g210m.
- When I check lspci | grep VGA, there is no Intel graphics card ?
```
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce G210M] (rev a2)
```- I installed ubuntu control center and check the VGA switching section, change VGA but it still says "High performance GPU is in use"
- I modified xorg.conf and used driver "intel" but I can't startx. Now im using driver "nouveau" instead
- I ran lscpi on ubuntu live CD but still no Intel graphics card ??

So, why there is no Intel graphics card listed in lspci ? and is there anyway I can add it into lspci so I can use intel driver instead of nouveau ?

Thank you in advance! Have a nice day!

---

### Post by sonee on 2011-03-06
ok, problem solved.

basically i updated the bios and the intel graphics driver ... suddenly disappeared. even in windows.
I downgraded bios through easy flash in bios, and ... tah dah :D

Thank you for reading.

---

