---
title: "erreur d'analyse syntaxique"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by m3asmi on 2009-08-06
I have problem in all new instalation 

i see this message in terminal :

____________________________________________________________________________________________


dpkg: error parsing in the file  « /var/lib/dpkg/available » near line 25173 package« libapm1 »:
  the field name «  » must be followed by a colon  ( : )  
 E: Sub-process /usr/bin/dpkg returned an error code (2)

____________________________________________________________________________________________

---

### Post by Partyboi2 on 2009-08-06
Hi, open a terminal (Applications>Accessories>Terminal) and try clearing the existing information about what packages are available
```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by m3asmi on 2009-08-06
> **Partyboi2 said:**
> Hi, open a terminal (Applications>Accessories>Terminal) and try clearing the existing information about what packages are available
```
sudo dpkg --clear-avail && sudo apt-get update
```


I do that 
this is the message: 

______________________________________________
...
Achieved [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com) jaunty-updates/multiverse Packages  
 Achieved [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com) jaunty-updates/multiverse Sources  
 50.1 kb approved 11s (4338o / s)  
 Reading package lists ... Made  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures could not be verified because the public key is not available: NO_PUBKEY A445E8CCD1A0D2FB 
 W: You can run 'apt-get update to correct these problems.
xxx@xxxxx:~$
______________________________________________





&&

 thinks for god
it's go now
 
now I can install the programs


:d:d:

---

### Post by Partyboi2 on 2009-08-06
> **m3asmi said:**
> I do that 
this is the message: 

______________________________________________
...
Achieved [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com) jaunty-updates/multiverse Packages  
 Achieved [http://ma.archive.ubuntu.com](http://ma.archive.ubuntu.com) jaunty-updates/multiverse Sources  
 50.1 kb approved 11s (4338o / s)  
 Reading package lists ... Made  
 W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures could not be verified because the public key is not available: NO_PUBKEY A445E8CCD1A0D2FB 
 W: You can run 'apt-get update to correct these problems.
xxx@xxxxx:~$
______________________________________________





&&

 thinks for god
it's go now
 
now I can install the programs


:d:d:
The gpg error is because you need to add the key, you can do this by opening a terminal and running these commands
```
gpg --keyserver keyserver.ubuntu.com --recv A445E8CCD1A0D2FB 
gpg --export --armor A445E8CCD1A0D2FB | sudo apt-key add -
```
then
```
sudo apt-get update
```

---

