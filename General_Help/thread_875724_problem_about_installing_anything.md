---
title: "problem about installing anything"
date: 2008-07-31
forum: General Help
---

### Post by efmaitnieh on 2008-07-31
today i installed ubuntu but when i try installing something like build essential package it gives error like that

sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential


how can i solve this problem
thanks

---

### Post by Rocket2DMn on 2008-07-31
Please run
```
sudo apt-get update
```
first.  If that doesn't help, please make sure you have repositories enabled from System->Administration->Software Sources
You probably want those first 4 boxes checked along with -security and -updates from the Updates tab.

---

### Post by Hunz on 2008-07-31
ive got the same issue here and i cant find this System-> Administration

i am using kubuntu 8.04, does that make a difference??

and another thing is, everytime i try installing anything it says missing libraries, so do i have to manually install them 1 by 1 ????

---

### Post by Rocket2DMn on 2008-07-31
Hehe, yes, that would make a difference.  I don't use KDE, but have a look here - [uhelp]community/Repositories/Kubuntu[/uhelp] - that should explain to you how to check repositories in Kubuntu.

---

### Post by hyper_ch on 2008-07-31
use Adept on Kubuntu or manually install synaptic.

```

sudo apt-get update && sudo apt-get install build-essential

```

---

