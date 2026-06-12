---
title: "Installing Package.Missing Dependencies."
date: 2008-09-28
forum: General Help
---

### Post by ashmew2 on 2008-09-28
Hi , 
I'm trying to install Anjuta (Its an IDE for C++) , but whenever i try in the terminal :

```
sudo apt-get install anjuta
```

it tells me :

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

The following packages have unmet dependencies:
  anjuta: Depends: libgdl-gnome-1-0 but it is not going to be installed
E: Broken packages


What should i do ? I really need to install Anjuta ...

Thanks..

---

### Post by zvacet on 2008-09-28
```
sudo apt-get install libgdl-gnome-1-0
```

or you can install it from synaptic.if that fails 

```
sudo apt-get -f install
```

---

### Post by ashmew2 on 2008-09-28
> **zvacet said:**
> ```
sudo apt-get install libgdl-gnome-1-0
```

or you can install it from synaptic.if that fails 

```
sudo apt-get -f install
```

Ive tried manually installing liubgdl-gnome but it fails saying it turn depends on libgdl-1-common or something..

Sudo apt-get -f install doesnt do anything at all...Just says 0 installed , 0 removed , 0 upgraded...

Ive also tried using aptitude and it tells me a solution with score -9882 but when i press Y to confirm , nothing happens...

Clueless as ever...

---

### Post by oldos2er on 2008-09-28
You have broken packages. To fix them you can do one of two things; run "sudo aptitude install -f" in a terminal, or go into Synaptic Package Manager, open the 'Edit' menu, and click 'Fix Broken Packages.'

---

### Post by ashmew2 on 2008-09-28
> **oldos2er said:**
> You have broken packages. To fix them you can do one of two things; run "sudo aptitude install -f" in a terminal, or go into Synaptic Package Manager, open the 'Edit' menu, and click 'Fix Broken Packages.'

Thanks for the suggestion but it didnt work out...It still says the same thing as i posted in the starting post...

By the way..did i mention im using Alpha 6 Intrepid ...

---

### Post by oldos2er on 2008-09-28
> **ashmew2 said:**
> Thanks for the suggestion but it didnt work out...It still says the same thing as i posted in the starting post...

By the way..did i mention im using Alpha 6 Intrepid ...

 You've got to expect problems to occur using alpha software. That said, maybe you can purge the broken packages and try again...?

---

### Post by cariboo on 2008-09-28
You might be better off remove the package and then using Synaptic to install it. I just installed anjuta with no dependency problems.

Jim

---

### Post by ashmew2 on 2008-09-29
> **oldos2er said:**
> You've got to expect problems to occur using alpha software. That said, maybe you can purge the broken packages and try again...?

well i dont exactly know how to purge it .. and yeah i know the risks involved , ive kept fedora as a backup os :)

---

