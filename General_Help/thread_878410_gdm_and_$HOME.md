---
title: "gdm and $HOME"
date: 2008-08-02
forum: General Help
---

### Post by elein on 2008-08-02
I'm new to ubuntu.  In the gdm environment HOME and other pertinent variables are not set.  It does not seem to source my .profile or .bash_profile.  The result is the term app has no $HOME, and firefox will not run w/o HOME set.  When I login to the console everything is fine.

I'm looking at Xsessions which appears to dot $HOME/.profile but I don't know if HOME is set at that point.

Suggestions, Ideas?  The gdm enviroment must have the basics set or nothing works.

--elein

---

### Post by pauper on 2008-08-03
Please, post the output:
```
env
set | grep -E '(^[[:upper:]])'
grep -E '(^[[:upper:]])' $HOME/.config/user-dirs.dirs
```

From bash manual, lines 75-86: 

> When bash is invoked as an interactive login shell, or as a non-interactive
shell with the --login option, it first reads and executes commands from the
file /etc/profile, if that file exists. After reading that file, it looks for
~/.bash_profile, ~/.bash_login, and ~/.profile, in that order, and reads and
executes commands from the first one that exists and is readable. The 
--noprofile option may be used when the shell is started to inhibit this
behavior.

When a login shell exits, bash reads and executes commands from the file
~/.bash_logout, if it exists.

When an interactive shell that is not a login shell is started, bash reads and
executes commands from /etc/bash.bashrc and ~/.bashrc, if these files exist.
This may be inhibited by using the --norc option. The --rcfile file option
will force bash to read and execute commands from file instead of
/etc/bash.bashrc and ~/.bashrc.

Add variables to /home/$USER/.bashrc .

An example:

```
echo "export DESKTOP=/home/john_doe/Desktop" >> ~/.bashrc
bash
echo $DESKTOP
/home/john_doe/Desktop
```

---

### Post by elein on 2008-08-03
The problem was my mismatched .profile and .bash_profile.  .profile was being executed as sh instead of bash and failing.

pauper, your post was very helpful.  Thank you.

---

