---
title: "more Makefile woes"
date: 2008-10-02
forum: General Help
---

### Post by Pipey on 2008-10-02
> pipey@Ubuntu:/home/orbithopper$ sudo make
g++ -c -o RaceEnd.o source/RaceEnd.cpp -I/usr/include/SDL -I/usr/include/GL -O3 -s
g++ -c -o Game.o source/Game.cpp -I/usr/include/SDL -I/usr/include/GL -O3 -s
g++ -c -o RaceM.o source/RaceM.cpp -I/usr/include/SDL -I/usr/include/GL -O3 -s
g++ -c -o AI.o source/AI.cpp -I/usr/include/SDL -I/usr/include/GL -O3 -s
g++ -c -o Init.o source/Init.cpp -I/usr/include/SDL -I/usr/include/GL -O3 -s
source/Init.cpp: In function ‘void initShaders()’:
source/Init.cpp:180: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:206: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:235: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp: In function ‘int initExt()’:
source/Init.cpp:312: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:312: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:312: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:312: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:312: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:312: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:359: error: ‘glXGetProcAddressARB’ was not declared in this scope
source/Init.cpp: In function ‘int InitTextures()’:
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
source/Init.cpp:582: warning: deprecated conversion from string constant to ‘char*’
make: *** [Init.o] Error 1




sad day.  

feedback??

---

### Post by tribaal on 2008-10-02
You might want to try passing -Wno-deprecated-declarations to gcc - it won't fix your problem, but it will certainly make the output more bearable :)

(I hope I'm not confusing the switch with another no-deprecated switch, there are so many :) )

Hope this helps

- Trib'

---

### Post by Pipey on 2008-10-02
> **tribaal said:**
> ...it won't fix your problem...

Hope this helps

- Trib'

no.

---

