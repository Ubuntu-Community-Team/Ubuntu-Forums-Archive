---
title: "SYNAPTIC doesn't see package from 3rd parts repositories"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by ^[H3ad-Tr1p]^ on 2009-04-28
hi

I've a problem with synaptic on my ubuntu jaunty x86_64 with gnome on my notebook

I've installed jaunty then I've performed apt-get update && apt-get dist-upgrade

then I've added new repositories of 3rd part software

I've put on my sources.list medibuntu ,googlepack ,wicd repos ecc eccc

after I've performed apt-get update I've tried to open synaptic to perform an installation of the software that I serve

[I]'ve noticed that in synaptic ,when I try to search  googleearth,skype ,picasa and other,in synaptic I can't find it.It find only a pacage that I can find in the default repositories


if I want to install ,for example,googleearth,skype and picasa I must to perform this operation from a command line with this command

sudo apt-get install googleearth picasa skype

at this point from a command line I can install these software

why? How I can solve this problem?

---

### Post by Marat Galiev on 2009-04-28
You add new sources from command promt(nano or vi)?
Or with synaptic?

---

### Post by ^[H3ad-Tr1p]^ on 2009-04-28
> **Marat Galiev said:**
> You add new sources from command promt(nano or vi)?
Or with synaptic?

yes,I had added new lines of 3rd parts with vim but also with gedit

xubuntu on my nettbook it isn't affect of this problem also I've added new lines of repositories from gedit or vim

---

### Post by jayachandranm on 2009-05-04
try 
> sudo aptitude update instead of > sudo apt-get update

that seems to have worked for me.

---

### Post by kostkon on 2009-05-04
> **'^[H3ad-Tr1p]^ said:**
> [I]'ve noticed that in synaptic ,when I try to search  googleearth,skype ,picasa and other,in synaptic I can't find it.It find only a pacage that I can find in the default repositories
> **'^[H3ad-Tr1p]^ said:**
> why? How I can solve this problem?
Because I assume you were using the quick-search feature in Synaptic. Use the regular search and you should be fine.

---

