---
title: "Passage Warty Breezy pb xserver"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by Kafi on 2005-12-29
Avant ça marchait sous warty, mais là ca revoit "impossible de démarrer le xserver" . Je pense que c'est un pb de carte graphique, donc j'installe le driver.
Donc sudo apt-get install nvidia-glx => Dépendance non satisfaite nvidia-kernel-1.0.7667=> J'essaye de l'installer=>Le paquet est un paquet virtuel il faut préciser lequel => Je choisi linux-restricted-modules-2.6.12-10-386 =>Dépend linux-restricted-modules-common mais ne sera pas installé=>J'essaye qd même de l'installer =>Dépend binutils-static=>Aucun paquet ne correspond à binutils-static, et là je suis bloqué.
Merci de votre aide. Théophile

---

### Post by Kafi on 2005-12-29
Petite précision, alors que avant j'avais internet, maintenant quand je fais un ping j'ai network unreachable. Je suis connecté en ethernet et internet marche... J'essaye sudo /etc/init.d/networking restart => reconfiguring network interfaces [OK]=> ping 192.168.0.1 network unreachable=> et qd je ping mon pc à partir d'un autre il n'e repond pas

---

