---
title: "Update failed since 2016"
date: 2021-11-06
forum: Hardware
---

### Post by cesarjules9123 on 2021-11-06
```
hp@faraj:~$ sudo apt update
sudo: impossible de déterminer le nom de l'hôte faraj: Aucun fichier ou dossier de ce type
[sudo] Mot de passe de hp : 
Désolé, essayez de nouveau.
[sudo] Mot de passe de hp : 
Err:1 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) xenial InRelease
  Connexion à 176.31.96.198: 8080 (176.31.96.198) impossible. - connect (111: Connexion refusée)
Err:2 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease
  Impossible de se connecter à 176.31.96.198:8080 :
Err:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
  Connexion à 176.31.96.198: 8080 (176.31.96.198) impossible. - connect (111: Connexion refusée)
Err:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial InRelease                     
  Connexion à 176.31.96.198: 8080 (176.31.96.198) impossible. - connect (111: Connexion refusée)
Err:5 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  Impossible de se connecter à 176.31.96.198:8080 :
Err:6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  Impossible de se connecter à 176.31.96.198:8080 :
Err:7 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) xenial-security InRelease
  Impossible de se connecter à 176.31.96.198:8080 :
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-fr_FR) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-fr) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  Connexion à 176.31.96.198: 8080 (176.31.96.198) impossible. - connect (111: Connexion refusée)
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  Impossible de se connecter à 176.31.96.198:8080 :
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  Impossible de se connecter à 176.31.96.198:8080 :
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  Impossible de se connecter à 176.31.96.198:8080 :
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/xenial/InRelease](http://archive.canonical.com/ubuntu/dists/xenial/InRelease)  Connexion à 176.31.96.198: 8080 (176.31.96.198) impossible. - connect (111: Connexion refusée)
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/xenial/InRelease)  Connexion à 176.31.96.198: 8080 (176.31.96.198) impossible. - connect (111: Connexion refusée)
W: Failed to fetch [http://ppa.launchpad.net/wine/wine-builds/ubuntu/dists/xenial/InRelease](http://ppa.launchpad.net/wine/wine-builds/ubuntu/dists/xenial/InRelease)  Impossible de se connecter à 176.31.96.198:8080 :
W: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-fr_FR) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-fr) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:48 and /etc/apt/sources.list.d/xenial-partner.list:4
hp@faraj:~$ apt list --upgradable
```

---

### Post by mIk3_08 on 2021-11-06
> **cesarjules9123 said:**
> hp@faraj:~$ sudo apt update
hp@faraj:~$ apt list --upgradable
Can you run the given command below in your Linux Ubuntu Operating System terminal please. And Paste the result here in thread wrap with code. Thanks a lot.
```
hostnamectl status
```

---

### Post by TheFu on 2021-11-06
xenial support ended last April. Those repos are gone.
You waited too long.
Backup anything you don't want to lose and do a fresh install of 20.04. Then restore your data.
20.04 support ends in April 2025.  You'll need to move to a new LTS **BEFORE** that date.  22.04 will be an LTS and released April of next year.  24.04 will also be an LTS and released April of 2024, so you'll have 2 more opportunities to migrate to a new LTS BEFORE support ends.

Waiting until after support has ended means extra hassles.  That is the take-away.

Or you can pay Canonical for ESM support of 16.04 to get a few more years. of support.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

### Post by Dennis N on 2021-11-06
> Or you can pay Canonical for ESM support of 16.04 to get a few more years
It's no charge for individuals to maintain 16.04 security updates for up to 3 computers. 

Sorry, I can't see the failure to connect. Those links are active for me. It could be a temporary failure, or you could try choosing a different software archive.
You could also upgrade to 18.04.6 - Software Updater should be notifying you of this possibility.

---

### Post by cesarjules9123 on 2021-11-07
hp@faraj:~$ hostnamectl status
   Static hostname: faraj
   Pretty hostname: Faraj
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 6ae23a5a5dd40f76d2c9e66752a4acc6
           Boot ID: c17be1fc2e764c7e8e72cc6f1d211e25
  Operating System: Ubuntu 16.04 LTS
            Kernel: Linux 4.4.0-24-generic
      Architecture: x86-64

---

### Post by mIk3_08 on 2021-11-07
> **cesarjules9123 said:**
> hp@faraj:~$ hostnamectl status
   Static hostname: faraj
   Pretty hostname: Faraj
         Icon name: computer-laptop
           Chassis: laptop
        Machine ID: 6ae23a5a5dd40f76d2c9e66752a4acc6
           Boot ID: c17be1fc2e764c7e8e72cc6f1d211e25
  Operating System: Ubuntu 16.04 LTS
            Kernel: Linux 4.4.0-24-generic
      Architecture: x86-64
As what TheFu said, That the support of this xenial just ended up this year. Just try new LTS (Long Term Support) release. Good Luck. Regards.
> **TheFu said:**
> xenial support ended last April. Those repos are gone.
You waited too long.
Backup anything you don't want to lose and do a fresh install of 20.04. Then restore your data.
20.04 support ends in April 2025.  You'll need to move to a new LTS  **BEFORE** that date.  22.04 will be an LTS and released April of next  year.  24.04 will also be an LTS and released April of 2024, so you'll  have 2 more opportunities to migrate to a new LTS BEFORE support ends.
Waiting until after support has ended means extra hassles.  That is the take-away.
Or you can pay Canonical for ESM support of 16.04 to get a few more years. of support.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

