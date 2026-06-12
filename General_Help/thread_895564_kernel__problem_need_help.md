---
title: "kernel  problem need help?"
date: 2008-08-20
forum: General Help
---

### Post by dellboy on 2008-08-20
ok i got a kernel  problem with running  VirtualBox and vmware this what i get on VirtualBox. and vmware dose not even open 
can some please help me fix this i am running ubuntu 8.04.1. i use Liunx as my main os but some times i need to do some programing for college in windows. it be great if some could help me get this fixed  :D

[IMG]http://img93.imageshack.us/img93/5691/screenshotsb0.png[/IMG]

---

### Post by sdennie on 2008-08-20
What is the output of:

```

uname -a

```

Also, have you tried:

```

sudo apt-get install virtualbox-ose-modules-generic

```

---

### Post by dellboy on 2008-08-20
```

uname -a

```

i get >  2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux


Also, have you tried:

```

sudo apt-get install virtualbox-ose-modules-generic

```

i get this i had done this before 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  virtualbox-ose-modules-generic: Depends: virtualbox-ose-modules-2.6.24-20-generic but it is not going to be installed
E: Broken packages


---

### Post by sdennie on 2008-08-20
Ok.  I would try:

```

sudo apt-get update
sudo apt-get install virtualbox-ose-modules-generic

```

If that still fails, try:

```

sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic

```

---

### Post by dellboy on 2008-08-20
ok great i got virtualbox using 


> sudo apt-get install virtualbox-ose-modules-2.6.24-19-generic

and the update of packets 

any change of getting vmware working it just starts to load then closes :(

---

