---
title: "Freeze in librecalc, maybe due to graphics card"
date: 2012-07-06
forum: Hardware
---

### Post by pmatos on 2012-07-06
Hello,

I have a new system with an Ivy Bridge Intel HD Graphics 4000. I initially after installing 12.04 experienced some random freezes but after installing mesa-utils things got better. Now I managed to find a reproducible bug that freezes the PC. I checked this:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze/](https://wiki.ubuntu.com/X/Troubleshooting/Freeze/)

However, this doesn't apply because when the system freezes it goes offline, therefore I cannot ssh into it from another pc to get the logs. 

Maybe it is not graphics card?
Any suggestions?

The reason I think it is graphics card is because to reproduce it I just need to open libreoffice calc, create a 3000 row spreadsheet and then click and drag (to create a region) downwards. As new rows show up at the bottom very quickly suddenly it all freezes, net goes offline and screen just stays still.

Cheers,

Paulo Matos

---

