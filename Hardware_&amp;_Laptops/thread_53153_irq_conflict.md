---
title: "irq conflict"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by Thomvis on 2005-07-30
Greetings!
I'm a happy Ubuntu user since 5.04 came out, I use it allmost every day on my laptop. Today I decided to install Ubuntu on a secon pc. Windows XP was allready present and I made up a dual boot system (not difficult). Ubuntu is op and running and no harm is done to XP. But now I'm running on to some problems. The most annoying one is that I cant get my network running. I know what the problem is, but i dont know how to fix it. 
The problem is a IRQ conflict between my wireless card (on mini-pci) and my ATI Radeon. I discovered using windows that they where sharing IRQ bus 16. XP is working fine but it looks like Ubuntu can't handle a situation like this. I configured my wireless card (prism) correctly but I can't turn my card on. This is what i get:
```
#ifconfig eth0  up
SIOCSIFFLAGS. No such file or directory.
```

I tried to fix the conflict using some features in my BIOS but that doesn't seem to work. Or my BIOS is incapable of such things or I can't find the right options.
Are their other ways to solve my problem?  I'll give more info/specs if needed..

Thanks in Advance,
Thomas Visser

---

