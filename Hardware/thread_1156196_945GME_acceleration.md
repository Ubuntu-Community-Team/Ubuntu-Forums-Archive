---
title: "945GME acceleration?"
date: 2009-05-11
forum: Hardware
---

### Post by mrzombie on 2009-05-11
Hello to all! I tried to look up information, and it's been over 2 hours of trial and error and it seems I can't get my card to accelerate even a little. I'm now working with a default of the Xorg.conf. I'd need a hand please?

---

### Post by Psicolonia on 2009-05-11
Intel? Is this Jaunty? Have you had problems with Intrepid? Jaunty is a bit buggy with Intel this release...

---

### Post by mrzombie on 2009-05-12
Jaunty UNR + EEEPC 1000HE. Yeah. So I guess I'm stuck without accel unless magical updates come around, not unlike santa, but before him this year I hope? :P Else I'll just install the 9.10 when it comes around and hope real hard that it will less break my intel stuff. And/or support the Fn + Stuff keys.

---

### Post by eldragon on 2009-05-12
hmm, 945 should work. there are many thing you can do..

i would first check xorg for error messages and strip xorg from them (finding solutions).

second: if using EXA accelmethod try UXA, if using UXA, try EXA....

of course you should have the intel drviers installed, and no ati / nvidia on your system...


if you dont have an xorg.conf file, generate one (cant remember how, a quick search will give you the means to)..


thats all i can think of..

good luck

---

