---
title: "[SOLVED] Can no longer update :'("
date: 2008-09-28
forum: General Help
---

### Post by Hyper Tails on 2008-09-28
Hi my computer runs hardy heron and i have an issue for some reason for updating

the update mangers show up a windows saying


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

and it closes

and what should i do?

please help with this issue

thank you

---

### Post by linux_lover69 on 2008-09-28
Try updating using this method through the terminal
[http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/](http://www.cyberciti.biz/faq/how-do-i-update-ubuntu-linux-softwares/)

---

### Post by Hyper Tails on 2008-09-28
not use if that was a solution to my problem

but i tried it and made my os not work before

any other advice?

---

### Post by gjoellee on 2008-09-28
Does upgrading in Temrinal work?
```
sudo apt-get upgrade
```

please post the output if it doesn't work :)

---

### Post by Hyper Tails on 2008-09-28
here it is

```
liam@liam-desktop:~$ sudo apt-get upgrade
[sudo] password for liam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
liam@liam-desktop:~$ 

```

---

### Post by linux_lover69 on 2008-09-28
try running
apt-get -f install

---

### Post by Hyper Tails on 2008-09-28
i already did but didn't fix the broken packages

but thanks though

---

### Post by linux_lover69 on 2008-09-28
hmm thats strange ill try to search around and see if i can find anything

---

### Post by Hyper Tails on 2008-09-28
i addtempeted the sudo apt-get upgrade thing and now this has happened

please help

i can't open compiz fusion icon or anything related to compiz

---

### Post by linux_lover69 on 2008-09-28
have you backed up any of your preferences. you might of messed something up and if you backed up it could fix it.

---

### Post by cariboo on 2008-09-28
Have you tried the broken package filter in synaptic. System--Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages?

Jim

---

### Post by Hyper Tails on 2008-09-28
for some reason i keep getting the fix broken packages after clicking for 5000 times

---

### Post by Hyper Tails on 2008-09-28
> **linux_lover69 said:**
> have you backed up any of your preferences. you might of messed something up and if you backed up it could fix it.

how do i do that?

---

### Post by linux_lover69 on 2008-09-30
well to back up your preferences you can get a program in the add/remove programs. just search backup and a backup preferences program should be there. If not make sure your showing all available applications at the top.

---

### Post by oldos2er on 2008-09-30
Can you run the following command, and if it shows errors, copy and paste them here?

sudo dpkg --configure -a

---

### Post by Hyper Tails on 2008-10-01
I reinstalled ubuntu and that worked.

---

