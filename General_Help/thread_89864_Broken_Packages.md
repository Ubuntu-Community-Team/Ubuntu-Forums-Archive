---
title: "Broken Packages ?"
date: 2005-11-13
forum: General Help
---

### Post by ne0_2k on 2005-11-13
Hi ,

i downloaded the amule deb package and it told me it required some dependencies i did not have : 
libstdc++6_4.0.2
libwxgtk2.6-0_2.6.1.2

i had a previous version of both and the Synaptic Package Manager didn't recognize any updates. so i d/l them from the amule site (as deb packages) and installed them. amule works but i get errors now in the package manager that some packages that depend on the "older" version have unmet dependencies now. 

anyone have any suggestions ?

---

### Post by taurus on 2005-11-13
I believe you can install amule directly with apt-get!!!  Why not do that and let apt-get take care of all the dependencies...

sudo apt-get install amule

---

### Post by ne0_2k on 2005-11-13
thanks taurus but i'm having the same problem anyway since i already installed the new packages. if i try to force the older version it wants to uninstall half of the packages i have. (its the gcc-4-base) 

the unmet dependencies i get for some reason are :

The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
  g++-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
  gij-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
  libgcj6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed
  libstdc++6-4.0-dev: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-2 is to be installed

what can i do ?

---

