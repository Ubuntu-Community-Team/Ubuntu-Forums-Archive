---
title: "server (with ubuntu desktop) problem"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by mazid on 2009-04-23
hello all i'm new here and i have a serious problem i my server 

i was unable to installing libc6-dev because of dependency problems (libc6 not compatible)
so i'v download libc6 and install it manually...somehow(?) when i strat to install it it begin to remove a lot of package after that i cant run synaptic (not even ls commande work) ..
i reboot the server and it does not work, my service provider try to fix to me (althought they dont provide soft support) and here what i get 

```
Voici les détails de cette opération : 
Réparation de la configuration logicielle
Date 2009-04-23 10:25:08, jonathan C a fait Réparation de
la configuration logicielle:
 serveur en erreur " Freeing unused kernel memory 384 k
freed. /sbin/init : /lib/libc.so.6 : version 'GLIBC-2.8'
not found required by /lib/libselinux.so.1. Kernel panic -
not syncing - attempted to kill init"
acces clavier bloqué
reboot hard avec meme erreur
reboot hard sur kernel dd avec meme constat
passage en rescue pour correction client
rescue ok
ping ok
ssh open 
``````
here is the detail of the operation : 
software configuration fixed
Date 2009-04-23 10:25:08,:
 serveur  error " Freeing unused kernel memory 384 k
freed. /sbin/init : /lib/libc.so.6 : version 'GLIBC-2.8'
not found required by /lib/libselinux.so.1. Kernel panic -
not syncing - attempted to kill init"
hard reboot with the same error
hard reboot in kernel dd with the same constant
switch to rescue mode for client fixing!!!
rescue ok
ping ok
ssh open 

```my question is simple, what should i do ?

i know that i've make so stupide action, but now any help will be really apreciated

---

### Post by mazid on 2009-04-23
well after some googling i.ve ssh access to the machine and i can install 

```
but when i try to update the system 
root@rescue:/# aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have unmet dependencies:
  libpopt0: Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
  libselinux1: Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
  language-support-writing-it: Depends: openoffice.org-thesaurus-it but it is not installable
  language-support-translations-de: Depends: openoffice.org-help-de but it is not installable
  libgnutls26: Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
  language-support-en: Depends: language-support-writing-en but it is not installable
  libpolkit-dbus2: Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
  dpkg: PreDepends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
  libglib2.0-0: Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
  language-pack-en: Depends: language-pack-en-base but it is not installable
  language-pack-pt: Depends: language-pack-pt-base but it is not installable
  language-pack-gnome-en: Depends: language-pack-gnome-en-base but it is not installable
  language-pack-gnome-nl: Depends: language-pack-gnome-nl-base but it is not installable
  language-pack-gnome-pl: Depends: language-pack-gnome-pl-base but it is not installable
  libpolkit2: Depends: libc6 (>= 2.8~20080505) but 2.7-10ubuntu3 is installed and it is kept back.
```

how can i install/repair libc6 ?

---

### Post by yeats on 2009-04-23
> so i'v download libc6 and install it manually...somehow(?)

So how did you install it?  Looks like you downloaded and installed an Ubuntu .deb package?  If so, you can remove it like you installed it with dpkg... (check man dpkg for more specific info about removing)

---

### Post by mazid on 2009-04-23
thanks for the reply chrissharp123 
well yes, but here is the problem during the installation many programs has removed 
after that i can't even run ls command, after rebooting nothing happen 

now this is the problem when  i try to run any command 
```

id: /lib/libc.so.6: version `GLIBC_2.8' not found (required by /lib/libselinux.so.1)
```and when i try to install lbc6 i get dependency problem 

```
Resolving dependencies...
open: 8453; closed: 4997; defer: 0; conflict: 15
```

---

### Post by yeats on 2009-04-23
You may have already decided this yourself, but if I were you, I would consider a total reinstall.  Sounds like libc is so integral to the system that nothing is going to work as expected.  I did this myself one time, replacing an essential library with a different version because something I was installing from source depended on it.  I ended up reinstalling myself.  It's probably easier than pulling your hair out trying to troubleshoot this! :-)

---

### Post by mazid on 2009-04-23
exactly this what have done :)
i have a new system now thinks for the reply

---

