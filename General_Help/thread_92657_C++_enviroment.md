---
title: "C++ enviroment"
date: 2005-11-20
forum: General Help
---

### Post by Theroninwins on 2005-11-20
HI  I got a small problem with C++. I installed the normal enviroment (i.e. what synaptic found when searching for c++) and now when I want to use some real basic function it says it doesn't know them:

#include <iostream.h>
#include <stdlib.h>
#include <stdio.h>
int main()
{
char mychar[100];
int i = 0;
//while the character is not a new line
while((mychar[i] = cin.get()) != '\n')
i++;

mychar[i] = NULL;
//display characters
cout<<mychar<<endl;

return 0;
}

It says after using g++:
test2.cpp:10: error: `cin' undeclared (first use this function)
test2.cpp:10: error: (Each undeclared identifier is reported only once for each
   function it appears in.)
test2.cpp:13: Warnung: converting to non-pointer type `char' from NULL
test2.cpp:15: error: `cout' undeclared (first use this function)
test2.cpp:15: error: `endl' undeclared (first use this function)


how come??

---

### Post by daganu on 2005-11-20
yes,

try to put this after the #includes:

using namespace std ;

this is what your linker are waiting for

---

### Post by Theroninwins on 2005-11-20
Ok thnaks that helped.... but I should have thought of that :-) damn....thanks

---

