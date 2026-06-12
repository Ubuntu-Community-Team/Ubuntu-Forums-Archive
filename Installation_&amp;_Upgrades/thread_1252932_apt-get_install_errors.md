---
title: "apt-get install errors"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by fjanoos on 2009-08-29
hi,

sometime ago while i was installing R on my system there was a power failure and the installation did not complete successfully. ever since then every time i try to run an apt-get install on any package i get the following error:


Setting up libreadline5-dev (5.2-3build1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libreadline5-dev (--configure):
 subprocess post-installation script returned error exit status 1
Setting up sshfs (1.9-1) ...
Errors were encountered while processing:
 libreadline5-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

i tried uninstalling and re-installing R - to no avail. i have tried hunting down this libreadline5-dev library - but i'm not very conversant with linux/ubuntu and don't know where to begin or how to fix it. 
this error is even preventing me from upgrading from 8.04 to 9.xx

any help will be appreciated.

thanks,
-fj

---

### Post by oldos2er on 2009-08-29
Have you tried **sudo dpkg --configure -a **?

---

### Post by fjanoos on 2009-08-30
Hi,
I tried the following - only to get the same error.

Any suggestions ?

[root] {~}>dpkg --configure -a
[root] {~}>apt-get install sshfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sshfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libreadline5-dev (5.2-3build1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing libreadline5-dev (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 libreadline5-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jerrrys on 2009-08-30
I can only point you to here

[http://www.google.com/search?q=Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+(1)+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Sub-process+%2Fusr%2Fbin%2Fdpkg+returned+an+error+code+(1)+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

[http://www.google.com/search?q=subprocess+post-installation+script+returned+error+exit+status+1+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=subprocess+post-installation+script+returned+error+exit+status+1+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

