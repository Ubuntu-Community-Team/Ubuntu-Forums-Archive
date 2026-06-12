---
title: "Su password?"
date: 2008-11-06
forum: General Help
---

### Post by Dumas32 on 2008-11-06
Hi!

I have installed Wubi and can normally login into wubi with my username&pw, but how can i get a su to install programms
e.g. apt-get install subversion

thx
Dumas

---

### Post by snowpine on 2008-11-06
Ubuntu uses 'sudo' instead of 'su'

For example:

```
sudo apt-get install subversion
```

The password is your regular user password.

---

