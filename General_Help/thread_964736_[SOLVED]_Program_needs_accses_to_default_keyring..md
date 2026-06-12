---
title: "[SOLVED] Program needs accses to default keyring."
date: 2008-10-31
forum: General Help
---

### Post by _sAm_ on 2008-10-31
Hi 

When I try to connect to my server with SSH(witch is using keys and not password), a dialogue pops up saying something that a program is asking for access to _default keyring_. I have two options(the screen gets locked down when this dialog is open), first to enter username + password or second to press Deny. First don't work at all, second work if I press it 3 to 4 times. After this SSH works just fine. 

The same happens if I try to mount a folder with sshfs, or if I want to look at the calendar at upper right corner of my screen. 

This starts to bug me. Do you know why it pops up(its new for me), and how I can stop it. 


Thanks for your help and sorry for my English.

---

### Post by _sAm_ on 2008-11-01
Nothing in seahorse that can change this, could I just uninstall seahorse?

Edit
I went to ~/.gnome2/keyrings directory and deleted the default keyring file. Next time I tried to use ssh it asked me for a new password and I just leaved it blank. Now the crap is gone.

---

