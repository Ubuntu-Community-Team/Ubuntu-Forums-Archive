---
title: "Removing Kernel Modules ?"
date: 2008-07-12
forum: General Help
---

### Post by EMCGFX on 2008-07-12
How can I remove or disable kernel modules without recompiling kernel it self. Right now I due this to unload modules temporarly. rmmod kvm_intel and rmmod kvm This way my VirtualBox works like a charm. But I am getting tired to type this every time I boot my pc. Is there a way to disable this modules in the config file or something? Thanks.

---

### Post by sdennie on 2008-07-12
You should be able to blacklist modules.  Have a look at the file /etc/modprobe.d/blacklist.  It's fairly straightforward and should allow you to manually load modules from the command line but prevent them from being loaded at startup.

---

### Post by EMCGFX on 2008-07-16
Nope that did not work. I am on Ubuntu 8.04.1 x64 between.

---

