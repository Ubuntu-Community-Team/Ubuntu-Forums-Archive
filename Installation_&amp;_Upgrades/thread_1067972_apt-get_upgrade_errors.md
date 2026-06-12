---
title: "apt-get upgrade errors"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by wojtek.bogusz on 2009-02-12
hi, i upgraded from 7.10 to 8.04 today and upgrade messed up my ldap configuration. it hang when trying to retrieve the ldap database backup. i managed to sort it all by hand but now each time i run apt-get i get message like below. how can i get rid of it? help... -- Wojtek

# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up slapd (2.4.9-0ubuntu0.8.04.2) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.3.35-1ubuntu0.3... done.
  Upgrading BDB 'checkpoint' options... .
  Moving old database directories to /var/backups:

  Backup path /var/backups/dc=frontline-2.3.35-1ubuntu0.3.ldapdb exists. Giving up...
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by zvacet on 2009-02-12
Try

```
sudo dpkg --configure slapd
```

---

### Post by wojtek.bogusz on 2009-02-13
> **zvacet said:**
> Try

```
sudo dpkg --configure slapd
```


thank you, but this will try to recofigure the package again. and it failed to do this already: "dpkg: error processing slapd (--configure)" (see above). also i do not want it to mess with the configuration. last time it did this during the 'apt-get upgrade' i had to manually solve all the problems it created. i just want to remove the need of configuration. i want to spot where is this information that "1 not fully installed or removed" package exist. and remove it. so when i run 'apt-get upgrade' it does not try to configure sldap. it runs clean. -- W

---

### Post by zvacet on 2009-02-14
>  i want to spot where is this information that "1 not fully installed or removed" package exist. and remove it. 

That package is slapd,because it is not installed (failed to configure).If you want you can remove it with 

```
sudo dpkg --remove --force-remove-reinstreq slapd
```

---

### Post by wojtek.bogusz on 2009-02-16
> **zvacet said:**
> That package is slapd,because it is not installed (failed to configure).If you want you can remove it with 

```
sudo dpkg --remove --force-remove-reinstreq slapd
```

hi, thank you. i think i have a difficulty of explaining myself :-) sorry! 

i do not want to remove the sldap package. i do need sldap. it is working ok now. and is configured well. i just want to remove the need of configuring this package that is written somewhere in apt-get/dpkg configuration settings/files. so apt-get runs clean. and i do not know how to clean those apt-get configuration files.

---

