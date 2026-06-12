---
title: "Unable To Update Hardy"
date: 2008-09-27
forum: General Help
---

### Post by joeyknuccione on 2008-09-27
When I try to get the automatic update feature to work, it starts off and maybe it is downloading packages, but it hangs. I have to do a ctr+alt+backspace and log in again to get it to stop. Is this related to my synaptic only working from the command line? How do I fix this?

---

### Post by prince_niceguy on 2008-09-27
May your update-manager package is corrupt. Try reinstalling it, it might fix the issue.

---

### Post by DougieFresh4U on 2008-09-27
you could try the terminal:

```
sudo apt-get -f install 
sudo dpkg --configure -a
```

---

### Post by joeyknuccione on 2008-09-27
'Preciate the help!

sudo apt-get -f install shows:

sudo: unable to resove host joe-laptop

...0 upgraded...

sudo dpkg --configure -a shows:

sudo: unable to resolve host joe-laptop


I got no clue here what's up?

---

