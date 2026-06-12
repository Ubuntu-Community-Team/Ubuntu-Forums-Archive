---
title: "[SOLVED] gconf gnome-power-manger&amp;gt;cpufreq setting missing in intrepid"
date: 2008-11-05
forum: General Help
---

### Post by Andreas1 on 2008-11-05
gconf apps>gnome-power-manger>cpufreq
that key set the default cpu scaling policy for ac and dc. see also here: [http://ubuntuforums.org/showthread.php?t=597998&highlight=powernowd]("http://ubuntuforums.org/showthread.php?t=597998&highlight=powernowd")
for example, on hardy i told it to use ondemand on ac and powersave on dc power.

i can't find this setting anywhere in intrepid, where did it go?

---

### Post by chrisccoulson on 2008-11-05
It's gone. Upstream decided to remove this functionality from gnome-power-manager. See [this blog entry]("http://www.advogato.org/person/mjg59/diary.html?start=123") for the rationale behind this decision

---

### Post by Andreas1 on 2008-11-05
For those who were wondering (like me), in short:

Basically it says that ONDEMAND (=adjusting the cpu frequency to the cpu load) will be more power-efficient than POWERSAVE regardless of the power situation. This is because the difference in power consumption between idle and processing time does weigh enough to justify using ONDEMAND to get the processing done as fast as possible, thus resulting in more power-saving idle time.

thanks for the link!

i am not sure though if they took my fan into account...

---

### Post by beercz on 2008-11-05
Thanks for this guys.  I didn't realise.  Until now, I have been using the CPU Frequency applet to adjust from OnDemand to Powersave when running my laptop on battery.

From reason given it looks like I don't need to do this any more.

---

### Post by beercz on 2008-11-05
Ooops - double post - my apologies

---

