---
title: "compiz (extra plugins)"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by MatthewWaterman on 2009-08-24
Hi I am really new to Ubuntu 
I am trying to install the extra plugins but I get this

matthew@matt:~$ sudo apt-get install compiz-bcop compiz-dev libtool build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libgl1-mesa-dev libglu1-mesa-dev autoconf intltool xsltproc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
[COLOR=Red]E: Package compiz-bcop has no installation candidate[/COLOR]
matthew@matt:~$ 

HELP!

---

### Post by stlsaint on 2009-08-24
have you tried installing from the repos?

---

### Post by junke1990 on 2009-08-24
had this one in a somewhere a long time ago but what was it...

try to update the packages and if possible open the GUI synaptic and try to install it with him in the hoop he will present a solution.

what repos/ppa did you get the package from? cant seem to find in synaptic...

good luck with you compiz!

---

### Post by stlsaint on 2009-08-24
> **MatthewWaterman said:**
> Hi I am really new to Ubuntu 
I am trying to install the extra plugins but I get this

matthew@matt:~$ sudo apt-get install compiz-bcop compiz-dev libtool build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libgl1-mesa-dev libglu1-mesa-dev autoconf intltool xsltproc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz-bcop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  compiz-fusion-bcop
[COLOR=Red]E: Package compiz-bcop has no installation candidate[/COLOR]
matthew@matt:~$ 

HELP!


i found the file you are referring to in my repos: "compiz-fusion-bcop"...its a "compiz option code generator" is what repos describe it as...now i will tell you that i run compiz with animations and all and i do not have this package installed on my system!

---

### Post by stlsaint on 2009-08-24
> **junke1990 said:**
> had this one in a somewhere a long time ago but what was it...

try to update the packages and if possible open the GUI synaptic and try to install it with him in the hoop he will present a solution.

what repos/ppa did you get the package from? cant seem to find in synaptic...

good luck with you compiz!


im using jaunty based kernel...are you asking for a list of my source file?

---

### Post by junke1990 on 2009-08-24
yes in which ppa or repos it is? I regularly add ppa's to my souces.list

---

### Post by stlsaint on 2009-08-24
> **junke1990 said:**
> yes in which ppa or repos it is? I regularly add ppa's to my souces.list



im using multiuniverse, main restricted, jaunty universe, and security universe!!! start update manager and see what options you have checked for sources list to update...i.e its going to be some of the options i listed above here!!

---

### Post by junke1990 on 2009-08-24
got him! enabled the rest of the repos ty :)

---

### Post by stlsaint on 2009-08-24
> **junke1990 said:**
> got him! enabled the rest of the repos ty :)


no prob...just here to help!

---

### Post by MatthewWaterman on 2009-08-24
Got it sorted thank-you everyone! :) 
Cheers!

---

