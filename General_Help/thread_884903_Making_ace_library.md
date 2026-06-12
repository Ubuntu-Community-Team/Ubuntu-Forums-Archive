---
title: "Making ace library"
date: 2008-08-09
forum: General Help
---

### Post by dawn_to_dusk_[pt] on 2008-08-09
hi everyone.

i've getting some errors i don't understand what they mean because i've heard of macros on linux, maybe someone could help me.

```
dawn2dusk@toshibuu:~/ACE_wrappers/ace$ make
make[1]: Entering directory `/home/dawn2dusk/ACE_wrappers/ace'

GNUmakefile: /home/dawn2dusk/ACE_wrappers/ace/GNUmakefile.ACE MAKEFLAGS=w

make[1]: Leaving directory `/home/dawn2dusk/ACE_wrappers/ace'
make[1]: Entering directory `/home/dawn2dusk/ACE_wrappers/ace'
ACE_FlReactor will not be built due to one of the following disabled make macros:
x11 gl fl

GNUmakefile: /home/dawn2dusk/ACE_wrappers/ace/GNUmakefile.ACE_FlReactor MAKEFLAGS=w

make[1]: Leaving directory `/home/dawn2dusk/ACE_wrappers/ace'
make[1]: Entering directory `/home/dawn2dusk/ACE_wrappers/ace'
ACE_QtReactor will not be built due to one of the following disabled make macros:
qt

GNUmakefile: /home/dawn2dusk/ACE_wrappers/ace/GNUmakefile.ACE_QtReactor MAKEFLAGS=w

make[1]: Leaving directory `/home/dawn2dusk/ACE_wrappers/ace'
make[1]: Entering directory `/home/dawn2dusk/ACE_wrappers/ace'
ACE_TkReactor will not be built due to one of the following disabled make macros:
tk

GNUmakefile: /home/dawn2dusk/ACE_wrappers/ace/GNUmakefile.ACE_TkReactor MAKEFLAGS=w

make[1]: Leaving directory `/home/dawn2dusk/ACE_wrappers/ace'
make[1]: Entering directory `/home/dawn2dusk/ACE_wrappers/ace'
ACE_XtReactor will not be built due to one of the following disabled make macros:
x11 xt

GNUmakefile: /home/dawn2dusk/ACE_wrappers/ace/GNUmakefile.ACE_XtReactor MAKEFLAGS=w

make[1]: Leaving directory `/home/dawn2dusk/ACE_wrappers/ace'
make[1]: Entering directory `/home/dawn2dusk/ACE_wrappers/ace/SSL'
SSL will not be built due to one of the following disabled make macros:
ssl

GNUmakefile: /home/dawn2dusk/ACE_wrappers/ace/SSL/GNUmakefile.SSL MAKEFLAGS=w

make[1]: Leaving directory `/home/dawn2dusk/ACE_wrappers/ace/SSL'
dawn2dusk@toshibuu:~/ACE_wrappers/ace$ 


```

i did not found on the "internetz" how to enable these macros, or what even they mean! 

i also can login in normal gnome or xfce sessions, i've always to login into failsafe sessions. there is any way to know why this is happening ? 

best regards

---

### Post by amitkumar133 on 2010-02-18
Hi,

I am also getting these errors while building ACE libs. Can anyone suggest the workaround? The 1st message is very old and I guess the creator or some other person would have got the solution to this problem. 
Any help would be highly appreciated.

Amit

---

