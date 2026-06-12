---
title: "[SOLVED] Conky shell script"
date: 2008-08-22
forum: General Help
---

### Post by eddVRS on 2008-08-22
Hi,

I've recently started playing around with Conky (which rules), and would like to add to the display some of my CLI aliass (for example).

Does anyone know how to do this, or anywhere I can read up on using bash scripts (not used them before) so I can create one and drop it into ~/.conkyrc?

Any help muchly appreciated!
Thanks

---

### Post by Diabolis on 2008-08-22
You can execute whatever you want with the **exec** variable. There are some other variations of it too. Check the [documentation]("http://conky.sourceforge.net/documentation.html") and the [variables list]("http://conky.sourceforge.net/variables.html")

> 
**exec**
Executes a shell command and displays the output in conky. warning: this takes a lot more resources than other variables. I'd recommend coding wanted behaviour in C and posting a patch.

---

### Post by eddVRS on 2008-08-23
thanks Diabolis! I was struggling with the shebangs in my script files.
Thanks!

---

