---
title: "no Audio"
date: 2010-04-27
forum: Hardware
---

### Post by k15h0re on 2010-04-27
I installed ubuntu 9.10 on my HP Dv-6 2155tx...there is no audio...cud ne1 help

---

### Post by devicerandom on 2010-04-27
Just to triage...

What audio card is it? (post **lspci** output if unsure)

Have you tried to unmute stuff with **alsamixer** from a command line?

---

### Post by lidex on 2010-04-28
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

