---
title: "How to compile C at gcc?"
date: 2008-10-03
forum: General Help
---

### Post by david sousa on 2008-10-03
hey! im learnig c language but i dont know how to compile it.

I go at the terminal and i right gcc -c file and i get that file.o but i dont know how to run the program tha i v done

---

### Post by ahsile on 2008-10-03
If you do this:

gcc -o outputname sourcefile.c

You will get a result of "outputname" which will be executable. What you have done with the -c option is tell the compiler to *only* compile, but not link the executable.

When you are finished you should be able to execute your program with the command:

./outputname

For more complex builds, you should look up "make".

Hope this helps!

---

### Post by david sousa on 2008-10-03
It works! thanks

---

