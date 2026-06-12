---
title: "Help with java"
date: 2008-09-15
forum: General Help
---

### Post by skipsbro on 2008-09-15
I am currently learning how to program java via classes at my school, however my current compiler seems to hit an error (and I don't think my code has an error.

The code:
```
public class prog1
{

    public static void main(String args[])
    {
	System.out.print("Hello World!");
    }
}
```

And the terminal output when I compile (using gcj):

```
gcj prog1.java
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status

Compilation exited abnormally with code 1 at Mon Sep 15 17:34:05

```

Thanks in advance for any help that can be provided!

---

### Post by prince_niceguy on 2008-09-15
Have you tried using eclipse ide... one of the best ide around for java development. 

Also, try using sun jdk instead of gcj.

---

### Post by skipsbro on 2008-09-15
I've been using emacs, but it's worth checking out.

---

### Post by prince_niceguy on 2008-09-15
I am in software industry and I use eclipse for my development work. You can check it out. It is even in ubuntu repo. Using command line has its own advantage as you learn basics of how to compile and how to run a java class file etc. 

With eclipse you will code and be more productive and wont have to worry about compiling, classpath issues etc.

---

