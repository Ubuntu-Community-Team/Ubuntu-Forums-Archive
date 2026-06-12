---
title: "Subversion woes"
date: 2005-11-19
forum: General Help
---

### Post by patonw on 2005-11-19
I blindly let synaptic do an upgrade of my packages last night and I didn't see if subversion was changed, but all of a sudden, it's broken.

When I try to check out a tree from another computer everything ran smoothly until I used the local svn binary. At that point I got

> 
:p :~$ svn co svn+ssh://:p /home/;) /.svn/test test2
svn: Can't open file '.svn/entries': No such file or directory
:p :~$ svn co svn+ssh://:p /home/;) /.svn/test test2
svn: Expected format '3' of repository; found format '4'


after which any sort of operation on the repository gives a 

> 
svn: Expected format '3' of repository; found format '4'


regardless of whether it was a local or remote. same output for any svnadmin operation.

Doing a little research it seems that format 4 is incompatible with pre-1.2.0 tools, but all of my binaries on all of my systems are 1.2.0 and yet I'm still getting that format 3 is what is expected.

How the heck do I get it to stop expecting format 3?

---

