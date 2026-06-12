---
title: "R8169 Problems"
date: 2011-06-25
forum: Hardware
---

### Post by guytryis on 2011-06-25
Can these output cause me the problems?
"
root@guy-desktop:/home/guy# lsmod | grep 8169
r8169                  34140  0 
mii                     4381  1 r8169
"
Why i got mii?can this is be the origin of my problems?

---

### Post by gordintoronto on 2011-06-25
What problems are you having?

Google found this: "The r8169 module needs the MII hardware support library."

---

