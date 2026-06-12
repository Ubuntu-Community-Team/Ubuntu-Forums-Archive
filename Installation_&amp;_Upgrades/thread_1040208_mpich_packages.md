---
title: "mpich packages?"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by florian100 on 2009-01-15
hay (for reasons I can't see at the moment it is working now... so the thread is solved...thank you)
I am trying to understand a program and the first step is to compile it and change different thinks. But I have already some problems at this state. The makefile is called lcdm_gas.Makefile. After consulting make help I think the makefile can be used with 

make --makefile=lcdm_gas.Makefile

or am I wrong?
The error message is

root@base:$ make --makefile=parameterfiles/lcdm_gas.Makefile
mpicci    -O3 -ip      -DPERIODIC  -DPEANOHILBERT -DWALLCLOCK    -DPMGRID=128 -DSYNCHRONIZATION -I/afs/rzg/u/vrs/gsl_linux/include -I/afs/rzg/u/vrs/fftw_linux/include    -c -o main.o main.c
make: mpicci: Command not found
make: *** [main.o] Error 127

Like you can see the file is using mpi. I thought I have some problems with mpich, but the installation seems to work (apt-get install mpich-bin). Is this the wrong package? Do I need additional packages?

I am using ubuntu 8.04

florian@base:/$ cat /proc/version
Linux version 2.6.24-23-generic (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu Nov 27 18:44:42 UTC 2008

florian@base:/$ uname -a
Linux base 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

thanks for help
and best regards
florian

---

