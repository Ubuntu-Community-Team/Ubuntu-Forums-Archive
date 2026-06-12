---
title: "measuring the cpu ticks"
date: 2008-11-10
forum: General Help
---

### Post by alluoshi on 2008-11-10
Hello,
I would like to calculate the cpu ticks of a certain process (since this process had been launched until this process had been  terminated). In other words, using the "top" command, I can know the cpu usage of this process as percentage. I want to translate the % cpu usage of this process to the number of ticks.
Any help please?

---

### Post by -Zeus- on 2008-11-10
well, some simple math *should* tell you this?  if it's using 10%, and the clock is 2000MHz, then 2000MHz * 10% = 200MHz?

edit: oh wait, you want to know the TOTAL since startup?  don't know how to help you there

---

### Post by alluoshi on 2008-11-10
yes, I want to know the total number of cpu ticks of a process when it is running. Secondly, if the cpu usage is %10, that doesn't mean %10 of its frequency. This means %10 of its capacity

---

