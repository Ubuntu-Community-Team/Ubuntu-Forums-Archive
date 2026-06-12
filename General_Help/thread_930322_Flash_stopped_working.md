---
title: "Flash stopped working"
date: 2008-09-25
forum: General Help
---

### Post by tstack77 on 2008-09-25
For some inexplicable reason flash stopped working for me earlier today and I only got an empty gray box. I went into synaptic and completely removed, then reinstalled flash, but now I get the prompt to install it with every website I visit. 

I tried the uninstall/reinstall again with no luck. What can I try now?

---

### Post by Forbees on 2008-09-25
try a few different flash players

---

### Post by tstack77 on 2008-09-25
Sorry, should wrote that I am trying this with "flashplugin-nonfree"

---

### Post by tstack77 on 2008-09-27
No ideas?

---

### Post by regor210 on 2008-10-01
I had the same problem with flashplugin-nonfree on my AMD x64 

$ sudo apt-get install java-gcj-compat-plugin

fixed it

I already had 
$ sudo apt-get install flashplugin-nonfree
$ sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre
installed

---

### Post by wolfen69 on 2008-10-01
just because you completely removed it, you still need to do: (after completely removing flash)
```
sudo apt-get clean
```and ```
sudo apt-get autoremove
```then reinstall flash. do this after uninstalling anything. if not, the file could still be in cache, and you would installing the same old file. (basically) plus it would clean out any corrupted dependencies.

---

