---
title: "Citizen CDS500 Printer, Rastor File not Compiling"
date: 2011-04-02
forum: Hardware
---

### Post by Robert_61 on 2011-04-02
Hello:

This is my first posting. I am running Ubuntu 10.10

I bought a Citizen CDS500 receipt printer. I downloaded the file, extracted it and copied it to a /work/ directory. 

In order to compile the rastortocds500.c file, I executed the following command in the /work/ directory:

ace@Front-Office:/work$ gcc -Wl,-rpath,/usr/lib -Wall -fPIC -O2 -o rastertocds500 rastertocds500.c -lcupsimage -lcups


I received the following error message:
rastertocds500.c:37: fatal error: cups/cups.h: No such file or directory
compilation terminated.

Should I create the missing directory and try again or is there something else I am missing? I am somewhat familiar with Ubuntu and Linux, but have never had to run any compilation programs.

Thanks

---

