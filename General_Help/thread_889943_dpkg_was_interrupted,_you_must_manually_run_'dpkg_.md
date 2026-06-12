---
title: "dpkg was interrupted, you must manually run 'dpkg --configure -a' ... help!"
date: 2008-08-14
forum: General Help
---

### Post by robcalewar on 2008-08-14
help; when i run the command "sudo apt-get install gtk+-2.0" I get the error "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem".

I can't add any new software, not through the add/remove software on the applications menu, terminal, nor synaptic package manger. Please help


nevermind I was stupid and added the quotes in the terminal. working fine now.

---

### Post by oldos2er on 2008-08-14
Run the command "sudo dpkg --configure -a"

---

