---
title: "Installing CMDiag"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by GISJason on 2008-12-14
Anyone have any ideas what could be going wrong here... I'm trying to get [cmdiag0.2]("http://sourceforge.net/projects/cmdiag/") installed but it won't work for some reason... It ends without a error code or telling me what's wrong...

```

slim@devlap:~/Desktop/cmdiag-0.2$ make
g++ -Wall -O2  -c cmdiag.cpp
cmdiag.cpp: In function ‘int main(int, char**)’:
cmdiag.cpp:28: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:29: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:30: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:31: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:45: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:45: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:211: error: ‘strstr’ was not declared in this scope
make: *** [cmdiag.o] Error 1
slim@devlap:~/Desktop/cmdiag-0.2$

```

TIA

---

