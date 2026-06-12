---
title: "Volume Controll"
date: 2008-08-27
forum: General Help
---

### Post by enzodad on 2008-08-27
Hi i shoudl say that i have the latest version of ubuntu. My volume controll does nothing lol. Im a linux noob. :) BUT I LOVE IT

---

### Post by Inane_Asylum on 2008-08-27
What computer/hardware are you running?

Also, run this command in a terminal and post the output:

```
grep Codec /proc/asound/card0/codec#*
```

---

### Post by enzodad on 2008-08-27
grep: /proc/asound/card0/codec#*: No such file or directory
(with  terminal)

---

### Post by Inane_Asylum on 2008-08-27
Try these, then, and post the results:

```
cat /proc/asound/cards
lspci
```

---

### Post by enzodad on 2008-08-27
0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21

---

### Post by Inane_Asylum on 2008-08-27
It'd still help to get the model of the computer or hardware you're using.  Someone with a similar/same sound controller got theirs working by the instructions at [http://makuchaku.info/amnesty/#configuresoundproperly](http://makuchaku.info/amnesty/#configuresoundproperly)

Keep us posted.

---

### Post by enzodad on 2008-08-27
GOing to give that a try. umm its dellgx280 1.5ram
p4 3.1HT

---

### Post by enzodad on 2008-08-27
Well did everything step by step ") :( no working still. I dont get it.

---

