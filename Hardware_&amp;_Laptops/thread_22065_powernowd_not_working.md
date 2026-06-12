---
title: "powernowd not working"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by lerrup on 2005-03-25
This was working beautifully but after being updated you could fry an egg on my laptop.  Any ideas?

---

### Post by fizgig on 2005-03-25
type "cat /proc/cpufreq"  (I think.  I'm at work right now).  Does that give you frequency info about your processor?  If not, post your processor info here and someone might be able to tell you what module to modprobe.

I didn't get anything from /proc/cpufreq until I modprobed "p4-clockmod".  Immediately afterward, I was able to read from /proc/cpufreq.

---

### Post by lerrup on 2005-03-27
I played around with kde and found the power part of the control centre which has allowed me to get this sorted.  I would recommend it to anyone with the same problem.  Is there anything similar for gnome?

---

### Post by songochain on 2005-03-27
[QUOTE=lerrup]I played around with kde and found the power part of the control centre which has allowed me to get this sorted.  I would recommend it to anyone with the same problem.  Is there anything similar for gnome?[/QUOTE]
 try this [http://zzrough.free.fr/emifreq.php](http://zzrough.free.fr/emifreq.php)

---

