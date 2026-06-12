---
title: "Linksys Wireless Adapter wont install"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by weedcali on 2009-09-18
Hello, im currently trying to install 9.04 on my spare maxtor 80gb hard drive. A big problem is that i dont have internet with it. I put my disk in the drive, open it up and click on the setup.exe icon and it gives me some kind of error window saying it was trying to extract it or something. It is a WMP11 card. Im completely new to Ubuntu and linux all together so idk what to do :confused:

---

### Post by Partyboi2 on 2009-09-18
Hi, Ubuntu does not run .exe files, to run .exe files you need to use a 3rd party program call wine. But you don't need wine to setup your wireless.
To get more information on your wireless card can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
lspci -v | less
```

---

