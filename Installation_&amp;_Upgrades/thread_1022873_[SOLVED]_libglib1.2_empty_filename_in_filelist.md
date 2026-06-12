---
title: "[SOLVED] libglib1.2 empty filename in filelist?"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by jlaurika on 2008-12-27
I cannot use any apt-get/synaptic/aptitude/update manager to update my 8.04 dapper. This is my fathers machine and Ubuntu wasnt being used in a while and it seems to have ~350 updates (dualboot winxp/ubuntu).

When ubuntu was started, i ran update manager and aptitude says:

> Noudin 154MB ajassa 1min15s (2038kB/s)                                                    
Puretaan malleja paketeteista: 100 %
Esiräätälöidään paketteja...
[B](Luetaan tietokantaa... dpkg: virhe käsiteltäessä libgtk1.2 (--remove):
 paketin `libglib1.2' tiedostoluettelo sisältää tyhjän tiedostonimen[/B]
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
Jonkin paketin asennus epäonnistui.  Yritän toipua:
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatietoja... Valmis       
Luen tilatietoja 

(Its mostly in finnish)
But basicly the bold part is same in every package manager. And translatef roughly it states:
"**(Reading database... dpkg: error handling libgtk1.2 (--remove) package 'libglib1.2' filelist includes empty filename**"

Like normally I tried to google for answers but found none. :/

---

### Post by Partyboi2 on 2008-12-27
Open a terminal and move the empty file list out of the way
```
sudo mv /var/lib/dpkg/info/libglib1.2.list  /var/lib/dpkg/info/libglib1.2.list.old
```then reinstall the package
```
sudo apt-get --reinstall install libglib1.2
```then
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jlaurika on 2008-12-29
> **Partyboi2 said:**
> Open a terminal and move the empty file list out of the way
```
sudo mv /var/lib/dpkg/info/libglib1.2.list  /var/lib/dpkg/info/libglib1.2.list.old
```then reinstall the package
```
sudo apt-get --reinstall install libglib1.2
```then
```
sudo apt-get update
sudo apt-get upgrade
```

Thanks, this worked.

---

