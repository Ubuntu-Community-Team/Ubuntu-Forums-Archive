---
title: "C++ question"
date: 2005-11-25
forum: General Help
---

### Post by nikolai.m on 2005-11-25
hi
i want to use Kate as editor...please tell me how i can compile? (would you be kind and as example use simple helloworld programm). i've tryed in terminal (Kate): g++ hello.cpp, but it didn't gave me anything

thnx

PS i got all build essentials installed!

---

### Post by bernardo on 2005-11-25
hello.
try this in a terminal (not Kate's, it may not work in Ubuntu because Kate is KDE and Ubuntu is Gnome), you must be in the directory your .cpp is stored in.

g++ -Wall yourprogram.cpp -o thenameyouwanttogiveit

or:

g++ -Wall -o thenameyouwanttogiveit yourprogram.cpp

You don't have to use the -Wall option but it gives your more debug info.

then type: ./thenameofyourprogram (don't forget the ./ :) )

for instance:

~> g++ helloword.cpp -o helloworld
or,
~> g++ -o helloword helloworld.cpp
or, if you want more debug info:
~> g++ -Wall -o hellowold helloworld.cpp

then to launch it:
~>./helloworld
Hello World !
~>


EDIT: an Helloworld example:

//helloworld.cpp
#include <iostream>
using namespace std;

int main() {
cout << "Hello World !" << endl;
}

---

### Post by nikolai.m on 2005-11-25
Thank you Bernardo....i can go on now with learning c++!
thnx again

---

### Post by nikolai.m on 2005-11-25
i tryed also Kdevelop. but whenever i add new class and compile it i get this:
[INDENT]/usr/bin/ld: Warning: size of symbol `main' changed from 73 in helloworld.o to 216 in ex1.1.o (numbers differ of course)[/INDENT]
and afterwords i can't compile anything!!!
can anyone explain me why's this happends?

---

