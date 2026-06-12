---
title: "installing psptoolchain"
date: 2008-11-07
forum: General Help
---

### Post by Dark_Sabre on 2008-11-07
I've gone through everything it's requested me to install with "sudo apt-get install" but, I get up to it requesting gmp. so I type "sudo apt-get install gmp" but it can't find it. any suggestions?

---

### Post by tacticalbread on 2008-11-07
hallo thar Dark_Sabre.

try this: 
```

sudo apt-get install libgmp3-dev

```

you also need two other libraries, readline, and one other that I can't remember.

so just use this:

```

sudo apt-get install libgmp3-dev libreadline5

```

---

### Post by Dark_Sabre on 2008-11-07
I shall try that thanks xitherun

---

### Post by tacticalbread on 2008-11-07
no problem. (:

I had this same problem when installing the toolchain, and I used Synaptic to install the needed libraries.

I dunno if you can get to Synaptic in Xfce, but if you can, just search for the other library, and install it from there.

if you can't, let me know the name of the library.

---

