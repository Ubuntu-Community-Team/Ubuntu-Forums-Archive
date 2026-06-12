---
title: "[SOLVED] proble avec synaptic"
date: 2008-09-21
forum: General Help
---

### Post by freekdz on 2008-09-21
Bonjour, j'ai un probleme avec le gestionaire de paquets synaptic

quand je l'ouvre voila ce que j'ai

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

quand je fais: sudo dpkg --configure -a

voila la repance

Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
Cannot find /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1

merci

---

### Post by pytheas22 on 2008-09-21
Essayez:
```

sudo apt-get remove --purge initramfs-tools
sudo apt-get --configure -a
sudo apt-get install initramfs-tools
```

Ça marche maintenant?  Sinon on peut essayer d'autres choses.

(pour info: on vous demande d'écrire en anglais ici, pour que plus de monde puisse le lire et répondre, donc si vous savez parler anglais, merci de vien vouloir répondre en anglais.  Sinon on peut continuer cette fois en français...)

---

### Post by freekdz on 2008-09-21
voila la repance que j'ai us
freekdz@freekdz-desktop:~$ sudo apt-get remove --purge initramfs-tools
[sudo] password for freekdz: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
freekdz@freekdz-desktop:~$ sudo apt-get --configure -a
E: L'option --configure de la ligne de commande n'est pas reconnue
freekdz@freekdz-desktop:~$ sudo apt-get --configure -a
E: L'option --configure de la ligne de commande n'est pas reconnue
freekdz@freekdz-desktop:~$ sudo apt-get install initramfs-tools
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
freekdz@freekdz-desktop:~$ 

j'ai meme essayer sa:

freekdz@freekdz-desktop:~$ sudo dpkg remove --purge initramfs-tools
dpkg: requiert une option d'action

Taper dpkg --help pour une obtenir une aide sur l'installation et la désinstallation des paquets [*]*;
Utiliser «*dselect*» ou «*aptitude*» pour gérer le paquets de manière
plus conviviale*;
Taper dpkg -Dhelp pour une obtenir une liste des valeurs drapeaux de débogage*;
Taper dpkg --force-help pour consulter la liste des options de forçage*;
Taper dpkg-deb --help pour une obtenir une aide sur la manipulation des fichiers *.deb*;
Taper dpkg --licence pour voir la licence copyright et l'absence de garantie (GNU GPL) [*].

Les options marquées d'un [*] affichent beaucoup d'informations - tubez-les à travers «*less*» ou «*more*».
freekdz@freekdz-desktop:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
Cannot find /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ sudo dpkg install initramfs-tools
dpkg: requiert une option d'action

Taper dpkg --help pour une obtenir une aide sur l'installation et la désinstallation des paquets [*]*;
Utiliser «*dselect*» ou «*aptitude*» pour gérer le paquets de manière
plus conviviale*;
Taper dpkg -Dhelp pour une obtenir une liste des valeurs drapeaux de débogage*;
Taper dpkg --force-help pour consulter la liste des options de forçage*;
Taper dpkg-deb --help pour une obtenir une aide sur la manipulation des fichiers *.deb*;
Taper dpkg --licence pour voir la licence copyright et l'absence de garantie (GNU GPL) [*].

Les options marquées d'un [*] affichent beaucoup d'informations - tubez-les à travers «*less*» ou «*more*».
freekdz@freekdz-desktop:~$ 


dsl je ne sais pas m'exprimer en anglais je comprend un peut mais j'arrive pas a m'exprimer merci pour la comprehention

---

### Post by pytheas22 on 2008-09-21
> voila la repance que j'ai us
freekdz@freekdz-desktop:~$ sudo apt-get remove --purge initramfs-tools
[sudo] password for freekdz:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
freekdz@freekdz-desktop:~$ sudo apt-get --configure -a
E: L'option --configure de la ligne de commande n'est pas reconnue
freekdz@freekdz-desktop:~$ sudo apt-get --configure -a
E: L'option --configure de la ligne de commande n'est pas reconnue
freekdz@freekdz-desktop:~$ sudo apt-get install initramfs-tools
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
freekdz@freekdz-desktop:~$

j'ai meme essayer sa:

freekdz@freekdz-desktop:~$ sudo dpkg remove --purge initramfs-tools
dpkg: requiert une option d'action

Eh excusez-moi, j'ai bien fait erreurs dans mes instructions (j'ai mis 'apt-get' au lieu de 'dpkg')...mais vous les avez bien remplacées avec les bonnes commandes, qui malheuresement quand même n'ont pas réussi.

Alors, quelle reponse avez vous pour les commandes:
```

sudo dpkg --configure -a --force-all
sudo aptitude -f remove
sudo dpkg --configure -a
```

> 
dsl je ne sais pas m'exprimer en anglais je comprend un peut mais j'arrive pas a m'exprimer merci pour la comprehention 

C'est pas grave on va continuer ici en français (si vous excusez mes erruers grammaticales...c'est pas ma langue maternelle), mais pour info il y a également des [forums français]("http://forum.ubuntu-fr.org/"), pour la prochaine fois.

---

### Post by freekdz on 2008-09-22
voila j'ai essayer les commande le resultats:
freekdz@freekdz-desktop:~$ sudo dpkg --configure -a --force-all
[sudo] password for freekdz: 
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
Cannot find /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ sudo aptitude -f remove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Lecture de l'information d'état étendu      
Initialisation de l'état des paquets... Fait
Construction de la base de données des étiquettes... Fait
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
freekdz@freekdz-desktop:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
Cannot find /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
update-initramfs: failed for /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ 


j'ai essayer de poster dans le forum français mais jai pas us de repance
merci bcp

---

### Post by Ryadt on 2008-09-22
Restart ton PC.
Puis essais
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by freekdz on 2008-09-22
voila j'ai essayer :(:
freekdz@freekdz-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for freekdz: 
Atteint [http://playonlinux.botux.net](http://playonlinux.botux.net) hardy Release.gpg
Ign [http://playonlinux.botux.net](http://playonlinux.botux.net) hardy/main Translation-fr                     
Ign [http://depot.jeuxlinux.fr](http://depot.jeuxlinux.fr) ./ Release.gpg                                   
Atteint [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                         
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-fr                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-fr              
Atteint [http://playonlinux.botux.net](http://playonlinux.botux.net) hardy Release                             
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy Release.gpg                         
Réception de*: 1 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/main Translation-fr [169kB]
Atteint [http://archive.canonical.com](http://archive.canonical.com) hardy Release                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Atteint [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg                      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-fr                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-fr        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-fr          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-fr        
Atteint [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                          
Ign [http://depot.jeuxlinux.fr](http://depot.jeuxlinux.fr) ./ Translation-fr                                
Atteint [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                 
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-fr                         
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-fr             
Atteint [http://deb.opera.com](http://deb.opera.com) lenny Release                                     
Ign [http://depot.jeuxlinux.fr](http://depot.jeuxlinux.fr) ./ Release                                       
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                      
Atteint [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                    
Ign [http://playonlinux.botux.net](http://playonlinux.botux.net) hardy/main Packages                           
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Atteint [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                     
Atteint [http://playonlinux.botux.net](http://playonlinux.botux.net) hardy/main Packages                       
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                     
Atteint [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                
Ign [http://depot.jeuxlinux.fr](http://depot.jeuxlinux.fr) ./ Packages                                      
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages          
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                 
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources           
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources             
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages            
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://pok3d.net](http://pok3d.net) ./ Release.gpg                                            
Ign [http://pok3d.net](http://pok3d.net) ./ Translation-fr                                         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                        
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-fr                   
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://pok3d.net](http://pok3d.net) ./ Release                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Atteint [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources                     
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Atteint [http://depot.jeuxlinux.fr](http://depot.jeuxlinux.fr) ./ Packages                                  
Ign [http://pok3d.net](http://pok3d.net) ./ Sources                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-fr                         
Atteint [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages                    
Ign [http://pok3d.net](http://pok3d.net) ./ Packages                                               
Atteint [http://pok3d.net](http://pok3d.net) ./ Sources                                            
Réception de*: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Atteint [http://pok3d.net](http://pok3d.net) ./ Packages                                           
Réception de*: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Réception de*: 4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Réception de*: 5 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Réception de*: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Atteint [http://download.skype.com](http://download.skype.com) stable/non-free Packages                     
Réception de*: 7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Réception de*: 8 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Réception de*: 9 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]               
Réception de*: 10 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]              
Réception de*: 11 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]              
Réception de*: 12 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]              
Réception de*: 13 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/restricted Translation-fr [2790B]
Réception de*: 14 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/universe Translation-fr [194kB]
Réception de*: 15 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                           
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release.gpg                         
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy/cairo-dock Translation-fr           
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                            
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-fr                   
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release                             
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy/cairo-dock Packages                 
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                         
Atteint [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy/cairo-dock Packages             
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                           
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                
Atteint [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                
Réception de*: 16 [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/multiverse Translation-fr [3614B]
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates Release.gpg  
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/main Translation-fr
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/restricted Translation-fr
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/universe Translation-fr
Ign [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/multiverse Translation-fr
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy Release               
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates Release                     
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/main Packages                       
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/restricted Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/restricted Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/main Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/multiverse Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/universe Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/universe Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/multiverse Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/main Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/restricted Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/restricted Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/main Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/multiverse Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/universe Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/universe Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/multiverse Packages
369ko réceptionnés en 5s (67,6ko/s)  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
freekdz@freekdz-desktop:~$ 

merci

---

### Post by Sef on 2008-09-22
> dpkg --configure -a

Alors, quelle reponse avez vous pour les commandes:

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by freekdz on 2008-09-22
sef stp c pas pour être méchant mais ta lut les postes d'avant ou pas ?

merci

---

### Post by pytheas22 on 2008-09-22
Et si vous essayez:
```

sudo mkdir /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
sudo dpkg --configure -a
```

?

Il me semble que le problème, c'est que le programme 'update-initramfs' ne réussit pas parce qu'il cherche une directoire du nom '/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron' mais celui n'existe pas.

---

### Post by freekdz on 2008-09-22
freekdz@freekdz-desktop:~$ sudo mkdir /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
[sudo] password for freekdz: 
freekdz@freekdz-desktop:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
ln: `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron': lien direct non permis pour un répertoire
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
Cannot find /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
rm: ne peut enlever `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak': est un dossier
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ chmod 777 /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
chmod: modification des permissions de `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron': Opération non permise
freekdz@freekdz-desktop:~$ sudo chmod 777 /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
freekdz@freekdz-desktop:~$ sudo mkdir /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
freekdz@freekdz-desktop:~$ sudo chmod 777 /lib/modules/bootinitrd.img-2.6.15-52-server-bigiron
freekdz@freekdz-desktop:~$ sudo dpkg --configure -aParamétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
rm: ne peut enlever `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak': est un dossier
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ sudo rm /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak
rm: ne peut enlever `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak': est un dossier
freekdz@freekdz-desktop:~$ sudo chmod 777 /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak
freekdz@freekdz-desktop:~$ sudo rm /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak
rm: ne peut enlever `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak': est un dossier
freekdz@freekdz-desktop:~$ 
freekdz@freekdz-desktop:~$ sudo dpkg --configure -aParamétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
rm: ne peut enlever `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak': est un dossier
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
rm: ne peut enlever `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron.dpkg-bak': est un dossier
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
ln: `/boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron': lien direct non permis pour un répertoire
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
WARNING: Can't read module bootinitrd.img-2.6.15-52-server-bigiron: No such file or directory
sha1sum: /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron: est un dossier
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 1
freekdz@freekdz-desktop:~$

---

### Post by freekdz on 2008-09-22
c bon c regler j'ai suprimer les 2 dossiers sa a marcher 

freekdz@freekdz-desktop:~$ sudo dpkg --configure -a
Paramétrage de initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-bootinitrd.img-2.6.15-52-server-bigiron
WARNING: Can't read module bootinitrd.img-2.6.15-52-server-bigiron: No such file or directory
freekdz@freekdz-desktop:~$

---

### Post by pytheas22 on 2008-09-22
> c bon c regler j'ai suprimer les 2 dossiers sa a marcher


Qu'est-ce qui a marché?  Vous avez toujours un problème avec Synaptic ou non?  Si le problème reste, essayez:
```

sudo apt-get remove --purge initramfs-tools
sudo dpkg --configure -a
```

---

### Post by freekdz on 2008-09-24
non j'ai plus de probleme avec synaptic merci a tous

---

