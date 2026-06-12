---
title: "intel c++"
date: 2008-07-29
forum: General Help
---

### Post by junaid.kollam on 2008-07-29
I installed intel c++ compiler in ubuntu8.04.1 But i can't find it in system menu or anywhere else.Help me to find it out

---

### Post by DGortze380 on 2008-07-29
> **junaid.kollam said:**
> I installed intel c++ compiler in ubuntu8.04.1 But i can't find it in system menu or anywhere else.Help me to find it out

how did you install? compilers are usually command line utilities unless it's an IDE. just out of curiosity, why not gcc? it's included, works great.

```

g++ myProgram.cpp -o myProgram

```

---

### Post by beren.olvar on 2008-07-29
Normally they are installed in /opt/intel
look trough those directorys until you find some bin/ folder
inside are the executables, and also a file calles icpp.sh or something similar... there would be another one called just the same way, but .csh
run ./i????.sh (i dont know the exact name this file has) to export the variables needed to compile.
you can add a line in your .bashrc file to run it every time you call a terminal, so you can forgett about it.

cheers

---

