---
title: "&quot;Make&quot; error messages"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by tmussche on 2007-07-11
I installed Ubuntu 7.04 on a NEC laptop. The native screen resolution is 1400 x 1050, but because of an error in de Video BIOS i can't select this resolution. At a 1280x1024 resolution the image is all fuzzy. I found a website of a guy who uses Slackware on the same laptop and proposes a solution.

[http://65.78.2.122:8080/~jesse/NEC.html](http://65.78.2.122:8080/~jesse/NEC.html)

It uses a program 855resolution to fix it.

[http://perso.orange.fr/apoirier/](http://perso.orange.fr/apoirier/)

So i downloaded this program and tried to install it with make and make install as it sais in the manual.

Both commands give error messages like this (sorry in Dutch):
> cc -Wall -I`pwd` -DVERSION='"0.4"' -DPLUGINS='plugin1,plugin2,plugin3' -DREF_PLUGINS='&plugin1,&plugin2,&plugin3'    -c -o 855resolution.o 855resolution.c
855resolution.c:14:19: fout: stdio.h: Bestand of map bestaat niet
855resolution.c:15:20: fout: stdlib.h: Bestand of map bestaat niet
855resolution.c:16:20: fout: string.h: Bestand of map bestaat niet
855resolution.c:17:20: fout: unistd.h: Bestand of map bestaat niet
855resolution.c:18:20: fout: sys/io.h: Bestand of map bestaat niet
855resolution.c: In functie ‘find_modes’:
855resolution.c:31: fout: ‘NULL’ undeclared (first use in this function)
855resolution.c:31: fout: (Each undeclared identifier is reported only once
855resolution.c:31: fout: for each function it appears in.)
855resolution.c:42: let op: control reaches end of non-void function
855resolution.c: In functie ‘find_resolution’:
855resolution.c:53: fout: ‘NULL’ undeclared (first use in this function)
855resolution.c:54: let op: control reaches end of non-void function
855resolution.c: In functie ‘list_modes’:
855resolution.c:63: let op: impliciete declaratie van functie ‘printf’
855resolution.c:63: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘printf’
855resolution.c: In functie ‘parse_args’:
855resolution.c:79: fout: ‘NULL’ undeclared (first use in this function)
855resolution.c:81: let op: impliciete declaratie van functie ‘strlen’
855resolution.c:81: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘strlen’
855resolution.c:99: let op: impliciete declaratie van functie ‘atoi’
855resolution.c:101: let op: impliciete declaratie van functie ‘fprintf’
855resolution.c:101: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘fprintf’
855resolution.c:101: fout: ‘stderr’ undeclared (first use in this function)
855resolution.c:122: let op: impliciete declaratie van functie ‘strtol’
855resolution.c: In functie ‘usage’:
855resolution.c:130: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘printf’
855resolution.c: In functie ‘main’:
855resolution.c:140: fout: ‘NULL’ undeclared (first use in this function)
855resolution.c:147: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘printf’
855resolution.c:160: let op: impliciete declaratie van functie ‘iopl’
855resolution.c:161: let op: impliciete declaratie van functie ‘perror’
855resolution.c:172: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘fprintf’
855resolution.c:172: fout: ‘stderr’ undeclared (first use in this function)
855resolution.c:181: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘fprintf’
855resolution.c:190: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘fprintf’
855resolution.c:195: let op: impliciete declaratie van functie ‘putchar’
855resolution.c:206: let op: onverenigbare impliciete declaratie van ingebouwde functie ‘fprintf’
make: *** [855resolution.o] Fout 1


The 3rd line for example sais that the file stdio.h is not found. I don't know much about C/C++ but i recognize this as some kind of standard header file. Anyone knows what the problem here might be?

Thanks in advance!

Tim

---

### Post by tmussche on 2007-07-12
Already fixed. I used the 915resolution package instead. Info on:

[http://ubuntuforums.org/showthread.php?p=3008706#post3008706](http://ubuntuforums.org/showthread.php?p=3008706#post3008706)

Tim

---

### Post by oops6_4 on 2007-07-16
hi friends i m using ubuntu 7.04 in this i m trying to compile a simple c code 

#include<stdio.h>
void main(){
printf("hello")}

but while compiling this i get the error that stdio.h file not found

something like this

 $ gcc ab.c 
ab.c:1:18: error: stdio.h: No such file or directory
ab.c: In function ‘main’:
ab.c:3: warning: incompatible implicit declaration of built-in function ‘printf’
ab.c:3: warning: return type of ‘main’ is not ‘int’

wht will be solution for this please help...

---

### Post by DarkPontiac on 2007-07-16
> **oops6_4 said:**
> hi friends i m using ubuntu 7.04 in this i m trying to compile a simple c code 

#include<stdio.h>
void main(){
printf("hello")}

but while compiling this i get the error that stdio.h file not found

something like this

 $ gcc ab.c 
ab.c:1:18: error: stdio.h: No such file or directory
ab.c: In function ‘main’:
ab.c:3: warning: incompatible implicit declaration of built-in function ‘printf’
ab.c:3: warning: return type of ‘main’ is not ‘int’

wht will be solution for this please help...

From my C++ experience from school, i'm sure the file you include would be "iostream.h" without quotes and it would be "int main()" and not "void main()" without quotes.

I don't know if this applies to linux also. I know this applies to older windows builders

---

