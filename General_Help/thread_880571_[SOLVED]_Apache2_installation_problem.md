---
title: "[SOLVED] Apache2 installation problem"
date: 2008-08-05
forum: General Help
---

### Post by tyusoff on 2008-08-05
Hi guys,

I have been trying to install Apache2 on my 8.04 desktop. Is it an upgrade from 7.10. I have been using synaptic and also apt-get. But again and again these errors come up. Been doing updates n others. Hope someone can help me as I have been searching about this with no luck

```
tyusoff@CPDM:~$ sudo apt-get install apache2
Reading package lists... Done
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
  apache2: Depends: apache2-mpm-worker (>= 2.2.8-1ubuntu0.3) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.8-1ubuntu0.3) but it is not going to be installed or
                    apache2-mpm-event (>= 2.2.8-1ubuntu0.3) but it is not going to be installed
E: Broken packages

```

---

### Post by furlabs on 2008-08-05
Try:
```
apt-get install apache2 apache2-mpm-prefork
```

If that doesn't work, check your /etc/apt/sources.list and make sure all the entries say hardy, not gutsy. Then run:
```
apt-get update
apt-get -f install
```

---

### Post by tyusoff on 2008-08-05
Thanks, 

cleaning up the /etc/apt/sources.lst from gutsy helps me to install apache2 :)

---

