---
title: "gcc usage"
date: 2008-09-05
forum: General Help
---

### Post by evivek on 2008-09-05
Hi,
 I am new user of ubuntu as well as gcc.
 
I wrote simple program in c.
#include<stdio.h>
main()
{
 printf("hi");
}

and compiled using cc command.
I got error message saying somthing like this not able to find stdio.h.
idont know what to do plesae guide me.

---

### Post by overdrank on 2008-09-05
moved :)

---

### Post by ad_267 on 2008-09-05
Have you installed the build-essential package?
You can use synaptic package manager (System - Administration - Synaptic Package Manager) or:
```
sudo apt-get install build-essential
``` to install it.

---

