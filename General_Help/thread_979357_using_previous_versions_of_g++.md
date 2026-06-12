---
title: "using previous versions of g++"
date: 2008-11-11
forum: General Help
---

### Post by bla687 on 2008-11-11
Hello.

I'm working on a project for a class, and it compiles fine in the computer labs here, but I want to be able to work from home. I've got g++ configured correctly and can compile most of my projects, but some of the code I've been given for this project to build off of is a little old, I think. Anyway, when I try to run the makefile (attached) I get the following output:

g++  -g  -Wall  -c -o main.o main.cpp
In file included from /usr/include/c++/4.3/ext/hash_map:64,
                 from x3reader.h:11,
                 from main.cpp:13:
/usr/include/c++/4.3/backward/backward_warning.h:33:2: warning: #warning This file includes at least one deprecated or antiquated header which may be removed without further notice at a future date. Please use a non-deprecated interface with equivalent functionality instead. For a listing of replacement headers and interfaces, consult the file backward_warning.h. To disable this warning use -Wno-deprecated.
In file included from main.cpp:13:
x3reader.h: In member function ‘void X3Reader::ResetSkip()’:
x3reader.h:51: error: ‘INT_MAX’ was not declared in this scope
make: *** [main.o] Error 1

Like I said, it compiles fine on their computers (running red hat, not Ubuntu) and I think the problem is that I'm running g++ 4.3 and the labs have g++ 4.2. Anyway, I'm attaching the offending file (though I've gotten around this error and gotten one in another file telling me strcmp wasn't declared :mad: ) Anyway can I get around this error without modifying this header file? (I'm not supposed to modify it)

Thanks!

---

### Post by Yellow Pasque on 2008-11-11
You can install g++ 4.2
```
sudo apt-get install g++-4.2
```
Then change the symlink in /usr/bin to point to that instead of 4.3
```
sudo ln -sf /usr/bin/g++-4.2 /usr/bin/g++
```
Also, if you're using x86_64/amd64
```
sudo ln -sf /usr/bin/g++-4.2 /usr/bin/x86_64-linux-gnu-g++ 
```

---

### Post by bla687 on 2008-11-11
Oops, I forgot to attach the files. Oh well, it didn't matter, because that worked. Strange though, I tried changing g++ to g++-4.2 in the makefile (I had already installed 4.2). Now I just need to figure out which XML library they have on those computers.

Thanks!

---

