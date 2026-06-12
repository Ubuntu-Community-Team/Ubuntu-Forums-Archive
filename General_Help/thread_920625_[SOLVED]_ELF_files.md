---
title: "[SOLVED] ELF files"
date: 2008-09-15
forum: General Help
---

### Post by Tom Atkins on 2008-09-15
I downloaded Checkbook Tracker and uncompressed the tar gz file. The Readme file says the executable is an ELF file and to execute it from the command prompt. When I do that I get a command not found. I made the file executable but that did not help.

Any ideas?

---

### Post by koenn on 2008-09-15
when running executables from a location outside your PATH, like /home/me,  you either have to give an absolute path, like
/home/me/program

or make sure you're in the same directory as the program, and indicate 'current directory' with  ./

cd /home/me
./program

---

