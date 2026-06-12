---
title: "Have any software for enabling OpenGL version 3 or above in an GPU card version 2.1 ?"
date: 2022-05-28
forum: Hardware
---

### Post by aug7744 on 2022-05-28
Hello.
Thanks for read my topic.
In an notebook CPU Pentium P6100 have an Intel HD Graphics.
Not is simple figure what is the Intel HD Graphics model, but if is the first generation is OpenGL 2.1.
In Linux Ubuntu have any software allowing run OpenGL 3.x softwares in an GPU OpenGL 2.1 ?
I want test even if has an software that use CPU rendering.

Have an nice day.

---

### Post by &amp;KyT$0P# on 2022-05-28
> **aug7744 said:**
> run OpenGL 3.x softwares in an GPU OpenGL 2.1 ?
I want test even if has an software that use CPU rendering.

Try just running the program with [FONT=Courier New]LIBGL_ALWAYS_SOFTWARE=1[/FONT] environment variable set?  For example to do this with [FONT=Courier New]glxinfo[/FONT] in Terminal (which should show the OpenGL version) -
```
LIBGL_ALWAYS_SOFTWARE=1 glxinfo
```

---

### Post by aug7744 on 2022-05-28
Thanks very much for your reply.
I will test it.
Have an nice day.

---

### Post by mikewhatever on 2022-05-31
Pentium P6100 is rather old, its launch date being 2010. I am afraid OpenGL 2.1 is all it can do, and there is no way to enable version 3.

---

