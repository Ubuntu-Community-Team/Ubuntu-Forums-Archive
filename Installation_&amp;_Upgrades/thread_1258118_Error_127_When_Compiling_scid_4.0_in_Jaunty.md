---
title: "Error 127 When Compiling scid 4.0 in Jaunty"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by shy_guest on 2009-09-04
In 9.04 I downloaded & unzipped source code for scid 4.0 (version 3.6.1-2 available in Synaptic is from 2003 or thereabouts & 4.0 was released on 1st September 2009!).
I also installed  tcl8.5 & tk8.5 as per installation instructions by **sudo apt-get**.
I then autoremoved the tcl8.4 & tk8.4 as requested by the system.
I then navigated to the /home/me/Desktop/scid folder where I then typed
**sudo ./configure** which was successful. At the end of the process, system displayed  message saying
The Makefile configured for your system was written.
Now just type "make" to compile Scid.
As instructed I typed in
**make**
which concatenated a humungous number of files into a single file & then this tried to compile the single file with this result :

make: g++: Command not found
make: *** [src/pgnscid.o] Error 127

Is the compiler or link editor missing or what ?

---

### Post by Partyboi2 on 2009-09-05
Hi, have you installed the build-essential package?
```
sudo apt-get install build-essential
``` This will also install g++ which looks like you could be missing.

Even though it completed when you ran ./cofigure, check the last 10 lines that there were no errors or it complains of missing packages. If there are missing packages you will need to install them before running 'make'.

---

### Post by shy_guest on 2009-09-05
installed the build-essential package & the make went perfectly.
However when I tried to install scid, the followinw message appeared :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tcl8.4 tk8.4
Suggested packages:
  tex-chess tclreadline
The following NEW packages will be installed:
  scid tcl8.4 tk8.4

tcl8.4 & tk8.4 were removed previously at the system's request when I got the tcl8.5 & tk8.5 ones.
**What ???**

---

### Post by swoody on 2009-09-05
Hi, again! I just came across this thread, so I figured I'd stop in and say hi. Thanks again for dropping by #ubuntu-beginners-help, and remember if you ever have any other questions you can always swing by, and we'd be glad to help you out :)

Best of luck finding that English bash scripting book, too!

---

