---
title: "Cant install nrg4iso"
date: 2008-07-17
forum: General Help
---

### Post by sheepsheds1 on 2008-07-17
Dear all.

I recently downloaded the source for nrg4iso and extracted it to /usr/local/src. However when I looked for the configure file there wasnt one there and when I changed to the directlry in the terminal and typed in ./configure and error message was displayed "can't find folder".

I have searched the forums and google for this and would really appreciate some feedback. 

I also tried make, and sudo make install - both with error messages also. 

How would I compile this source?

---

### Post by dracayr on 2008-07-17
hi,

did you cd into /usr/share/src/appName/ before running configure?
not all programs use configure, sometimes it's called autogen.sh instead or it just doesn't exist. In that case you only have to run make and make install

dracayr

---

### Post by Yannick Le Saint kyncani on 2008-07-17
Hi, don't know about nrg4iso, but there is a nrg2iso available in ubuntu's repos. It may suit you fine ?

---

### Post by sheepsheds1 on 2008-07-17
errrm well if there is one in the repos i may as well install it that way it would be much easier as the source is a bit of a jumble for me. Thanks guys for the quick responses. Its great for us who don't have the experience of you super users - god i'd love to able to do everything on linux!

---

### Post by sheepsheds1 on 2008-07-17
i did change to the extracted directory cd /usr/local/src/nrg4nero. There is no configure file but when I  issued "make" the following was displayed: 

anubis@anubis-desktop:/usr/local/src/nrg4iso$ make
gcc -Os -Wall   -c -o main.o main.c
In file included from main.c:39:
iso.h:44: error: expected specifier-qualifier-list before ‘uint8_t’
In file included from main.c:40:
nrg.h:51: error: expected specifier-qualifier-list before ‘uint64_t’
nrg.h:59: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
nrg.h:59: error: expected declaration specifiers or ‘...’ before ‘uint64_t’
main.c: In function ‘main’:
main.c:182: error: ‘uint64_t’ undeclared (first use in this function)
main.c:182: error: (Each undeclared identifier is reported only once
main.c:182: error: for each function it appears in.)
main.c:182: error: expected ‘;’ before ‘trk_offset’
main.c:183: error: expected ‘;’ before ‘nrg_length’
main.c:184: error: ‘uint32_t’ undeclared (first use in this function)
main.c:184: error: expected ‘;’ before ‘iso_length’
main.c:190: error: ‘trk_offset’ undeclared (first use in this function)
main.c:190: error: ‘nrg_length’ undeclared (first use in this function)
main.c:190: error: too many arguments to function ‘nrg_trackdata’
main.c:203: error: expected ‘;’ before ‘copy_length’
main.c:204: error: expected ‘;’ before ‘fill_length’
main.c:211: error: ‘iso_length’ undeclared (first use in this function)
main.c:212: error: ‘PVD_t’ has no member named ‘volumeId’
main.c:215: error: ‘copy_length’ undeclared (first use in this function)
main.c:216: error: ‘fill_length’ undeclared (first use in this function)
make: *** [main.o] Error 1



Any ideas anyone?

---

### Post by dracayr on 2008-07-17
the output of ls? some README or INSTALL file?

dracayr

---

### Post by sheepsheds1 on 2008-07-17
The output of ls is:


anubis@anubis-desktop:/usr/local/src/nrg4iso$ ls
description-pak  endian.h   iso.c  main.c    nrg.c         nrg.h
endian.c         globals.h  iso.h  Makefile  nrg_chunks.h


no install file or text file, not even an executable. 

Its confusing the hell out of me!

---

### Post by sheepsheds1 on 2008-07-22
I think that I might be closer to deciphering the problem. Thing is there is no makefile for the source which is used when creating the binary. 

So I'm looking into that at the moment. If anyone out there had any ideas I'm open to anything. Also, If anyone has any information on compiling source code in Linux, I would be most grateful.

Thanks guys and girlies

---

