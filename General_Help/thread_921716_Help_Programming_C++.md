---
title: "Help Programming C++"
date: 2008-09-16
forum: General Help
---

### Post by Cyberbanana1 on 2008-09-16
I am New to linux and programming. My main computer is a windows, but my teacher reccomends linux for the type of programs we are writing. I was wondering, is the terminal of linux the same as the the command prompt of windows, and if not, what is? also, does hardy heron come with a c++ compiler, and if not, where should i get one? thanks.

---

### Post by x300 on 2008-09-16
The command prompt in windows is like the little fragile batmobile that I played around with when I was a kid. The terminal in linux is the stuff that the REAL Batman acctually uses :)

You can install a c++ compiler by pasting this into a terminal:

> sudo apt-get install gcc

Then you compile your C++ code by typing:

> gcc -o outputfile file1.c file2.c file3.c

And run the compiled program by typing:

> ./outputfile

---

### Post by WRDN on 2008-09-16
Rather than installing gcc alone, it is better to install build-essential:

```
sudo apt-get install build-essential
```

Regarding Windows CLI vs Terminal (bash), I find the Terminal much (much) more powerful, and I now find I do most things in the Terminal, as it's fast, and very very powerful.

---

### Post by x300 on 2008-09-16
> **WRDN said:**
> Regarding Windows CLI vs Terminal (bash), I find the Terminal much (much) more powerful, and I now find I do most things in the Terminal, as it's fast, and very very powerful.

I agree. Once you get used to the terminal you'll almost stop using graphical programs. Well not entirely, but it was such a long time ago since I even opened Nautilus that I've forgotten what it looks like :)

---

### Post by Cyberbanana1 on 2008-09-16
Thanks lol. I followed the steps, and i made my own little program. You guys rock :guitar:

---

### Post by Iowan on 2008-09-16
I remember reading about **build-essential**.  I presume it has some desirable stuff - since it appears that **gcc** came pre-installed.

---

