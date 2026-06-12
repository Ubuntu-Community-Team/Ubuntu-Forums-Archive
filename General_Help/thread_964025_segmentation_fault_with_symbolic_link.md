---
title: "segmentation fault with symbolic link"
date: 2008-10-30
forum: General Help
---

### Post by PaulWhipp on 2008-10-30
Hi there,

I'm new to ubuntu but have played around with Unix/Linux in the past.

Setting up my system, everything is great and very impressive. To help me work, I set up my own bin directory and added it to my path but some applications have their own folders (e.g. ZendStudio) so...

I made a symbolic link to the Zend studio executable in my /bin -
ln -s ~/Applications... ~/bin/zs

so now typing zs opens up zend studio for me. cool!

Then I come back to the system after logging out and find that my symbolic link now just causes a 'segmentation fault' - no other info or feedback. Directly executing Zend Studio still works fine.

Anyone any idea what I've done wrong and/or how to investigate segmentation faults effectively?

---

### Post by PaulWhipp on 2008-11-11
Solving my own problem eventually - prefix any command causing the fault with strace eg:

strace zs

The result is verbose (grep can be handy) but it points one in the right direction (e.g. unable to write to some directory or other).

---

