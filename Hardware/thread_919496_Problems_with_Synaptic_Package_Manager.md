---
title: "Problems with Synaptic Package Manager"
date: 2008-09-14
forum: Hardware
---

### Post by primeabbadon on 2008-09-14
Hello,

When I want to go to System &#8594; Administration &#8594; Synaptic Package Manager and I want to install an application, I encounter this problem.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

The thing is that whatever application I want to remove or install, I get this message:

"Cannot remove 'gdebi'

One or more applications depend on gdebi. To remove gdebi and the dependent applications, use the Synaptic package manager."

The actual problem is the fact that I do not know how to manually remove something, since I am new with Linux.

Thank you in advance for your help.
Leo

---

### Post by cdtech on 2008-09-14
Run this command in a terminal:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

