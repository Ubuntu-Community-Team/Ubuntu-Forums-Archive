---
title: "Help with synaptic"
date: 2008-08-25
forum: General Help
---

### Post by maddcow87 on 2008-08-25
I keep getting the same error message, and then synaptic closes. any help appreciated!


E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by jerome1232 on 2008-08-25
I've seen this before that medibuntu.list is most probably messed up.
this way you can move it back if it were to screw things up worse:
```
sudo mv /etc/apt/sources.list.d/medibuntu.list ~/.medibuntu.list
sudo apt-get update
```
now try synaptic

---

### Post by maddcow87 on 2008-08-25
It worked, thanks!

---

### Post by jerome1232 on 2008-08-25
Welcome:)
since it worked go ahead and remove that file you shouldn't need it for anything

```
sudo rm ~/.medibuntu.list
```

---

