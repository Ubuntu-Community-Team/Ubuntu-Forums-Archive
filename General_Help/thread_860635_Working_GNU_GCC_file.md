---
title: "Working GNU GCC file?"
date: 2008-07-15
forum: General Help
---

### Post by epicbattle on 2008-07-15
I have been trying to find a compiler collection that will work and show up as a program from package manager, but all of the downloads don't seem to install or something. Does anyone know of a gcc filename that will indeed install itself? I'm new to Ubuntu, so I have not gotten the hang of installing the files myself through terminal and getting it to work. (I have tried that with the GCC, and was unsuccessful.) Thank you so much.

---

### Post by Vadi on 2008-07-15
Click [here]("apt:build-essential") to install gcc and all other basics you need to compile. If I understood you right.

---

### Post by epicbattle on 2008-07-16
Alright, tried to download the link, it said I already had "build essential", so I tried to find it anywhere on my computer, but I can't.

I un-installed Build essential it with package manager, and re-downloaded it hoping it might show up. Still couldn't find it. So I un-installed it again, and downloaded it through your link, but still no luck. Do I have to do something special to install and open it? Or is it not a program that you open? It just converts text into whatever? Sorry, I know I must sound like such an idiot, but I'm still brand new to Linux and pretty much know nothing. Thanks.

---

### Post by fyo on 2008-07-16
GCC is just a compiler (and some libraries), it's not an IDE.

If you want to see if you have a working GCC, just open a terminal window and type gcc.

If you don't mind me asking, what do you want to use gcc for? I'm not entirely clear on what you mean by "compiler collection"...

Anyway, gcc will compile c programs. In the simplest form, you just type:

```
$ gcc yourprogram.c
```

and it will return a file called a.out, which is the executable of yourprogram.

If you are looking for a complete IDE, you might want to give Eclipse a spin. It is available right from the repositories.

---

### Post by epicbattle on 2008-07-16
Well...I am trying to teach myself to program (in C or C++ right now). To my knowledge, and judging from that post I could be very wrong, I am supposed to have an actual program to compile code I write in txt. My actual ultimate goal is to build a robot... I hope that doesn't sound silly, but it's true. I don't have the money to go back to school for another degree, so I am using forums on the internet as my teachers. If you know of any other software that could help me in my endevours, then please, I am open to all suggestions.

---

### Post by arkara on 2008-07-16
> **epicbattle said:**
> Well...I am trying to teach myself to program (in C or C++ right now). To my knowledge, and judging from that post I could be very wrong, I am supposed to have an actual program to compile code I write in txt. My actual ultimate goal is to build a robot... I hope that doesn't sound silly, but it's true. I don't have the money to go back to school for another degree, so I am using forums on the internet as my teachers. If you know of any other software that could help me in my endevours, then please, I am open to all suggestions.

you must write a text file as you said, but you must save it, as name.c
then you must compile it by typing

```
gcc name.c
```

this will produce a binary file named a.out.
you can then execute it by typing
 
```
./a.out
```

gcc is on the repositories, and you can install it by typing 

```
apt-get install gcc
```

 as a root user.

---

### Post by spupy on 2008-07-16
GCC is collection of compilers - Gnu Compile Collection. It has compilers for both C and C++. 
If you don't want to use the command line, install **Geany**. It is a development environment, you write your code in it and click a button which invokes gcc on your code, so no need to type commands in terminal (you still can, of course). It offers other handy things like code completion, syntax highlighting, etc.

---

### Post by ilrudie on 2008-07-16
> **spupy said:**
> GCC is collection of compilers - Gnu Compile Collection. It has compilers for both C and C++. 
If you don't want to use the command line, install **Geany**. It is a development environment, you write your code in it and click a button which invokes gcc on your code, so no need to type commands in terminal (you still can, of course). It offers other handy things like code completion, syntax highlighting, etc.

I don't want to undermine what spupy said or try to start an argument but in my opinion the best way to learn c/c++ is using the command line.  Learn vi, gcc, make, checkstyle, and valgrind.  I've been out of school for a little while now and havn't taken a c programming class in half a decade but I'd guess these tools are still the standards.  Its good practice to call gcc with the -Wall and -ansi flags.  This will help insure you write clean standard code.  It will seem like a lot of work up front (vi is super powerful but has a nearly virtical learning curve -- buy a book or find a good online reference for vi) but if you are serious and you learn to code properly you will thank yourself later.  Good luck and happy learning.

---

### Post by spupy on 2008-07-16
> **ilrudie said:**
> I don't want to undermine what spupy said or try to start an argument but in my opinion the best way to learn c/c++ is using the command line.  Learn vi, gcc, make, checkstyle, and valgrind.  I've been out of school for a little while now and havn't taken a c programming class in half a decade but I'd guess these tools are still the standards.  Its good practice to call gcc with the -Wall and -ansi flags.  This will help insure you write clean standard code.  It will seem like a lot of work up front (vi is super powerful but has a nearly virtical learning curve -- buy a book or find a good online reference for vi) but if you are serious and you learn to code properly you will thank yourself later.  Good luck and happy learning.

I would recommend this workflow as well. :) I understood that OP is looking for a IDE like VisualWhatever from MS. If he wants to use IDE, ok. But a good C/C++ tutorial, which he needs, will with no doubt introduce the tools you mentioned. Starting from the basics. ;)

---

