---
title: "Another Update Problem"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by farimir on 2008-12-29
Please help

I try to update by using update manager and get the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to run "sudo dpkg --configure -a" from the terminal, but still get the following error:

farimir@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for farimir: 
Setting up doc-base (0.8.16) ...
read error at /usr/share/perl5/MLDBM.pm line 166.
dpkg: error processing doc-base (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


Please help, I am new to Ubuntu and cannot find a solution to my problem.

Thank you in advance!**[B]**[/B]

---

### Post by Aha2Y on 2012-05-04
Bump, I also got this problem with sudo apt-get install and the others. Any solution?

---

