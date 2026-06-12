---
title: "anjuta help"
date: 2008-10-22
forum: General Help
---

### Post by chillyair on 2008-10-22
This may be a very basic question but I don't know what else to do. I recently switched to linux a few months ago and downloaded anjuta so I could compile and run my old c programs I had written for a programming class. When I refer to the manual it says to choose Build -> compile from the top menu to compile your code. However the program window I get when I open anjuta doesn't have the build option in the top menu. I included a screenshot of the program window that I get which as you can see is pretty bare for options. Am I missing something? What do I have to do to be able to compile?

---

### Post by northern lights on 2008-10-22
I have no experience with anjuta, but it's just a GUI anyhow - i.e. it's most likely going to use the GNU C compiler, which you can invoke manually also.

In a terminal run```
gcc -c foo.c
```
This tells the compiler to run the preprocessor on the file foo.c and then compile it into the object code file foo.o. The -c option means to compile the source code file into an object file but not to invoke the linker.

If your entire program is in one source code file, you can instead run```
gcc foo.c -o foo
```This tells the compiler to run the preprocessor on foo.c, compile it and then link it to create an executable called foo. The -o option states that the next word on the line is the name of the binary executable file.

reference: [http://gcc.gnu.org/]("http://gcc.gnu.org/")

---

### Post by ajmorris on 2008-10-22
hi there,
not sure about your anjuta problem... but if you cant find the solution, you might like to try eclipse instead. (sudo apt-get install eclipse) It is a Java IDE that can program and compile many languages, including C.

AJ

---

