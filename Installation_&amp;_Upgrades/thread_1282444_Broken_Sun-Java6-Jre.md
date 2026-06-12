---
title: "Broken Sun-Java6-Jre"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Robots in Tibet on 2009-10-04
I tried to install sun-java6-jre last night, but when it came to the blue java screen that you're supposed to click ok on, I closed it off. Now it lists it as a broken package. I tried to run Synaptic and remove it through the broken filter, but when I do I get the error message:

"E: sun-java6-jre: Package is in a very bad inconsistent state - you should"

Any help would be greatly appreciated!

---

### Post by Robots in Tibet on 2009-10-04
Fixed it myself. Should'a looked harder in the forum search. :P

For those having trouble, I ran
sudo aptitude update

Press Y to let it install and insert the cd when it says. When the blue screen pops up, press TAB and OK. Should solve the problem.

---

### Post by paul1080 on 2009-10-26
I have the same error message trying to remove broken sun-java6-jre. Tried running sudo aptitude update but this has not solved the problem.

Any help would be greatly appreciated!

---

### Post by paul1080 on 2009-10-26
> **Robots in Tibet said:**
> Fixed it myself. Should'a looked harder in the forum search. :P

For those having trouble, I ran
sudo aptitude update

Press Y to let it install and insert the cd when it says. When the blue screen pops up, press TAB and OK. Should solve the problem.

Problem solved! 
I had to instead type in 
```
sudo apt-get -f install
```to get the install sequence you mention, didn't need the CD.

---

