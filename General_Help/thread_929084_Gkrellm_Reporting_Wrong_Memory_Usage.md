---
title: "Gkrellm Reporting Wrong Memory Usage"
date: 2008-09-24
forum: General Help
---

### Post by Mark76 on 2008-09-24
Either that or top is wrong.

Take a look at the screenshots included to see what I mean

---

### Post by Elfy on 2008-09-24
904168k is afaik 883Mb more or less, same with the swap figures

I would say that your swap is very big compared to your ram though

---

### Post by Mark76 on 2008-09-24
The relevant figures are;

Mem used.

GKrellm: 182 MBs
Top: 649844 KBs (whatever that is in Megs. It's certainly more than 182)

---

### Post by Elfy on 2008-09-24
I think it's the way that top reports it - I just looked at the totals :)

See what free -m says or install htop and check there

---

### Post by Mark76 on 2008-09-24
free -m says

free -m
             total       used       free     shared    buffers     cached
Mem:           882        659        223          0         35        402
-/+ buffers/cache:        221        661
Swap:         2580          0       2580

And this is the output from htop

---

### Post by Elfy on 2008-09-25
Can't read htop - but I really don't think it's anything to worry about.

---

