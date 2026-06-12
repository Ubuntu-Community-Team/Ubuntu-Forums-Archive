---
title: "CHMOD644  /.dmrc"
date: 2008-11-15
forum: General Help
---

### Post by bohica on 2008-11-15
Hi all, I'm getting a message on login that states that the /.dmrc file is being ignored and I have to be the only one that has read and write permissions abd that it should have 644. I have 
"chmod 644 .dmrc when in the home file but this hasn't resolved this, how do I fix this?

Thanks


Julian

---

### Post by bohica on 2008-11-16
SOlved

thanks to gary

To FIX type in the root terminal

Code:

chmod 644 .dmrc

then type (using YOUR user name for user)
Code:

chmod 700 /home/user

That should fix it!


:guitar:

---

