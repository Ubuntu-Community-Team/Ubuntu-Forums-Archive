---
title: "Two files dependent on each other"
date: 2008-09-27
forum: General Help
---

### Post by epq on 2008-09-27
--------------------------------------------------------------------------------

Hey,

I need to install libstd c++ v.5 but am running into difficulties with the dependancies of the necessary files. (v.6 came with ubuntu but I need v.5 to allow me to run a programme that is required by my university to allow access to the internet.)

I am not able to connect my laptop directly to the net so I have to download them individually on a different computer. 

On installing them, however, it seems that g++-3.3 depends on libstdc++5-3.3-dev and visa versa.

How does one overcome this?

Many thanks.

---

### Post by UbuWu on 2008-09-27
You need to install them both in one go, e.g. sudo dpkg -i *.deb

---

