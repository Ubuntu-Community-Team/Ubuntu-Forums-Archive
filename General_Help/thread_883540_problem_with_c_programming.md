---
title: "problem with c programming"
date: 2008-08-08
forum: General Help
---

### Post by charanpreethu on 2008-08-08
if i compile a c program "error: stdio.h: No such file or directory"
error occurs......what am i supposed to install???

---

### Post by sharks on 2008-08-08
[http://linuxhelp.blogspot.com/2006/04/steps-to-compile-c-c-programs-using.html](http://linuxhelp.blogspot.com/2006/04/steps-to-compile-c-c-programs-using.html)

---

### Post by lisati on 2008-08-08
> **charanpreethu said:**
> if i compile a c program "error: stdio.h: No such file or directory"
error occurs......what am i supposed to install???
Try the following from the terminal/Konsole:
```
sudo apt-get build-essential
```
This should take care of the problem.

---

### Post by charanpreethu on 2008-08-08
i have gcc 4.2.3.......but still its not working if i compile error will be shown

---

### Post by agapito on 2008-08-08
The file you need is  /usr/include/stdio.h
If it is not there install the build-essential metapackage like lisati said.

---

### Post by charanpreethu on 2008-08-08
how can i check whether that file is present or not???

---

### Post by agapito on 2008-08-08
open a terminal and type

ls /usr/include/stdio.h

if it is not there the shell will complain.  You can open a nautilus (file browser) window and navigate to /usr/include and see if the file is there.

Go ahead and install the build-essential anyway. It won't hurt you. You might prefer to use synaptic (it's in System -> Administration) to search for the package and install from there.

---

### Post by charanpreethu on 2008-08-08
ya i istalled that.......i checked it out using terminal....now im gettin diff error...ofr below program

#include<stdio.h>


int main()
{
int a=1;
pritnf("%d",a);
}

if i compile it using cc test.c or gcc test.c im gettin

/tmp/ccQrlNXK.o: In function `main':
test.c:(.text+0x1d): undefined reference to `pritnf'
collect2: ld returned 1 exit status

what shall i do now???

---

### Post by Bachstelze on 2008-08-08
You're having a typo, it's [font="Courier new"]printf[/font].

---

### Post by charanpreethu on 2008-08-08
wat am i supposed to do???

---

### Post by ad_267 on 2008-08-08
Umm, change pritnf to printf.

Try and figure things out for yourself. The error messages explain what's wrong.

---

### Post by charanpreethu on 2008-08-08
oops sorry tat was a very silly mistake...sorry and thank you....

---

### Post by Archimedes0212 on 2008-08-08
you also have your main function returning an int although you have no return statement in your main function.

---

### Post by howlingmadhowie on 2008-08-08
if you write the following function definition:

int main() { /* some program text here *}

you should end it with a return statement, for example:
```

#include <stdio.h>

int main() {
  int a=4;
  printf("%d\n", a);
  return 0;
}

```

if you compile the program and tell the compiler to show you all the problems, even if they aren't critical ( gcc program.c -Wall), it will complain about a missing return statement if you don't do this.

---

