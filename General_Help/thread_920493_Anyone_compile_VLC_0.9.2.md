---
title: "Anyone compile VLC 0.9.2?"
date: 2008-09-15
forum: General Help
---

### Post by AaronMT on 2008-09-15
Just curious what libraries are required for the compile? I tried looking on the videolan website but it did not list.

Thanks in advance,

AaronMT

---

### Post by arch0njw on 2008-09-16
This will get you the build dependencies:  sudo apt-get build-dep vlc

You should be prompted if you want to install these, so you can choose 'n' not to.

Otherwise, it appears that their wiki is down due to high load.

---

### Post by Meow27 on 2008-09-25
```
sudo apt-get build-dep vlc
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

aside from that my configuration goes thrugh.. its just i get arrors all of the sudden in the middle of the build and i dont know what to do :( (hardy)

---

### Post by jimmy the saint on 2008-09-25
so you have another package manager running?  two instances of apt cannot run at the same time.  Close all synaptic and "add/remove programs" instances and try again

---

### Post by jmszr on 2008-09-25
If you google Tombuntu, you will find what you are looking for in his website.

---

