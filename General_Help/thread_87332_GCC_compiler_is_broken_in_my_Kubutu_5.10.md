---
title: "GCC compiler is broken in my Kubutu 5.10"
date: 2005-11-07
forum: General Help
---

### Post by wildscribe on 2005-11-07
I just installed Kubutu 5.10 and everything had been working fine until I tried to 
compile a basic C program and it doesn't work. 

Here is the test program:

#include <stdio.h>

int main(void)
{
    printf("Howdy out there!\n");
    return 0;

}

I saved it as hello.c and compiled it like this gcc hello.c -o hello 

and Then I got the error messages below:

wildscribe@wildskubuntu:~/cstuff$ gcc hello.c -o hello
hello.c:1:20: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

Anyone got  a suggestion for how to fix this problem. I downloaded and installed
the GCC compiler using "apt-get install gcc" and it installed gcc version 4.0

Thanks!

- - - Wild

---

### Post by ltmon on 2005-11-07
Could you try

> sudo apt-get install build-essential

That should make sure you have absolutely everything you need to compile.

L.

---

### Post by dtfinch on 2005-11-07
Maybe try "apt-get install build-essential".

I would have thought just installing gcc would install the standard headers though.

---

### Post by wildscribe on 2005-11-07
**SUCCESS!** The command - *sudo apt-get install build-essential* **worked!**

Thank you both! You made my night.. my week... and my month!!! Now I can
use Kubuntu for all my programming needs. So long Fedora Core 4!!!

- - - Wild

---

### Post by az on 2005-11-07
Another happy customer....

---

### Post by ltmon on 2005-11-07
[QUOTE=azz]Another happy customer....[/QUOTE]

Do I get a sales commission?

---

### Post by az on 2005-11-08
[QUOTE=ltmon]Do I get a sales commission?[/QUOTE]
No.  Just everlasting gratitude.

---

### Post by KittyChunk on 2006-02-07
Nifty. 

build-essential fixed mine too after some random updates broke all the paths :)

---

### Post by mdb101 on 2006-02-07
Today I installed Ubuntu:-D , and I had problems with this too, but it works now. The only problem I'm having is running the a.out's....

maar@mpc:~/Desktop$ g++ example.cpp
maar@mpc:~/Desktop$ a.out
bash: a.out: command not found

clicking on the file doesn't help...:confused:

---

### Post by GeneralZod on 2006-02-07
[QUOTE=mdb101]Today I installed Ubuntu:-D , and I had problems with this too, but it works now. The only problem I'm having is running the a.out's....

maar@mpc:~/Desktop$ g++ example.cpp
maar@mpc:~/Desktop$ a.out
bash: a.out: command not found

clicking on the file doesn't help...:confused:[/QUOTE]

Assuming a.out is actually created and placed in that directory (I always use the -o flag to specify an output filename), the command would be

```

./a.out

```

as the current directory is *never* in the path for security reasons.

---

