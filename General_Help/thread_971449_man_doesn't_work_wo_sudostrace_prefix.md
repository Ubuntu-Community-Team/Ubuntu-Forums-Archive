---
title: "man doesn't work w/o sudo/strace prefix"
date: 2008-11-05
forum: General Help
---

### Post by kernelsanders on 2008-11-05
every time I run man <anything>, I get the response:
man: invalid option -- F
Try `man --help' or `man --usage' for more information.

I don't type the 'F'. 
There's no alias in my .bashrc file.
This doesn't occur when I precede the man with sudo, strace, or ltrace. 

How do I even start to troubleshoot this? What could be the problem?

I'm using Hardy Heron. Plenty of ram, HDD space, 2.8 GHz Pentium D processor

---

### Post by kernelsanders on 2009-01-17
turns out that although there wasn't an alias there was a man() function in the bashrc file i downloaded. once i commented this out everything worked.

---

