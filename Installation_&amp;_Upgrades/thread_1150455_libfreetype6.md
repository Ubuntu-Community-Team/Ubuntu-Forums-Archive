---
title: "libfreetype6?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by lwpro on 2009-05-06
When I want to install the gtk2.0-dev&#65292; I encounter I a dependence problem as:
```
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
E: Broken packages

```
When I try to find what the problem is, in the end I get the libfreetype6-dev can't be installed as:
Its dependence is 
```
libfreetype6 (= 2.3.9-4build1) but 2.3.9-4ubuntu0.1 is to be installed
```
So I can't figure out how to do it, can anyone help? I use the official source and want to compile emacs23 from cvs~ btw, I am using jaunty

---

### Post by zvacet on 2009-05-06
```
sudo apt-get -f install
```

---

### Post by rhaces on 2009-05-08
> **zvacet said:**
> ```
sudo apt-get -f install
```

I have the same probleme, i want to install Blackberry for Ubuntu and need libfreetype6-dev and cant do it, i follow your instructions and still cant't do it, here's what i get:

```
:~# apt-get install libfreetype6-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.9-4build1) but 2.3.9-4ubuntu0.1 is to be installed
E: Broken packages
:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~# apt-get install libfreetype6-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.3.9-4build1) but 2.3.9-4ubuntu0.1 is to be installed
E: Broken packages

```

Any Ideas???? BTW, I have Jaunty on!!!

---

