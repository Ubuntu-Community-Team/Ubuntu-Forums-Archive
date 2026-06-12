---
title: "Problems installing Omnett on Ubuntu 8.10"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by ronino on 2009-03-17
I have tried to install correctly Omnet++ 4.2 but it is impossible.
I have a couple of questions. I'll appriciate any kind of that someone could give to me.
Firs of all, my computer:

Computer:Vaio
Cpu: Intel Core 2 Duo t5500
Ram: 1Gb
S.O.: Ubuntu 8.10

I have installed most of compulsory dependencies of omnet
swig 1.3.38
Tcl/Tk -> 8.6 --- BLT2.4 doesn't work for Tcl/Tk 8.6 any ideas?
Java
MPI Mpich
pcap++

And I have tried to install akaroa as well.
I have set up the path
Finally I have configured and when I type make the final msg is:

===== Compiling sim ====
cd /home/ronin/omnetpp-4.0/src/sim && make
make[2]: se ingresa al directorio `/home/ronin/omnetpp-4.0/src/sim'
opp_msgc -Xnc -Xns sim_std.msg
opp_msgc - part of OMNeT++. (c) 2002-2005 Andras Varga
Translates .msg files into C++

Usage: opp_msgc [-s <cc-file-suffix>] [-t <h-file-suffix>]
[-I <dir> -I ...] [-h] <nedfile>
-I <dir> add directory to include path
-s <suffix> output C++ file suffix (defaults to: _m.cc)
-t <suffix> output C++ header file suffix (defaults to: _m.h)
-P <symbol> add dllexport/dllimport symbol to class declarations
-h output in current directory
make[2]: *** [sim_std_m.cc] Error 1
make[2]: se sale del directorio `/home/ronin/omnetpp-4.0/src/sim'
make[1]: *** [sim] Error 2
make[1]: se sale del directorio `/home/ronin/omnetpp-4.0'
make: *** [allmodes] Error 2


Thank you very much for your ideas.

---

