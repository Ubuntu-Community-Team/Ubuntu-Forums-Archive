---
title: "Total CPU Usage in CLI"
date: 2008-11-12
forum: General Help
---

### Post by belaviyo on 2008-11-12
Hi,

How can I find out total cpu usage.
I want some code which only shows total cup usage and then exit (not like top command), only total cpu usage, no more info

Thanks :)

---

### Post by mikjp on 2008-11-12
What about:
[FONT="Courier New"]
top -b -n1 | head -n 3 | tail -n 1| awk '{print $2}'[/FONT]

It runs top in the batch  mode for one iteration and shows the third line on console, finally awk prints the second column.

---

