---
title: "How do I track down where the environmental variables are set?"
date: 2008-08-14
forum: General Help
---

### Post by jonny5678 on 2008-08-14
Hi 

  I was wandering if it is possible to track down the origins of all the environmental variables listed when executing the "env" command. I need to change some variables that were set by programs on compilation.

---

### Post by cdtech on 2008-08-14
Most user configurations are stored within the user's home directory "cd ~". Most of them are within hidden directories with a leading ".". By issuing the "ls -lah" on the command line will list all directories as well as the hidden ones.

All configurations are per user and are stored within each user's home directory.

Hope this helps........

**P.S.**
If you need a more specific config location just post about which program you want to change.

---

### Post by Vivaldi Gloria on 2008-08-14
> **jonny5678 said:**
>   I was wandering if it is possible to track down the origins of all the environmental variables listed when executing the "env" command. I need to change some variables that were set by programs on compilation.

You can put your environ. var. in ~/.bashrc. Use the format

```
export ENVVAR=value
```

For example

```
export EDITOR=/usr/bin/nano
```

Use the command

```
source ~/.bashrc
```

after you make changes in .bashrc (or restart terminal).

---

