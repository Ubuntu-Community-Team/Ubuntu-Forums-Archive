---
title: "Issue with CPU frequency scaling on core duo T2600"
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by vfanelia on 2006-07-21
Hi,

I just installed the Dapper 6.06 on my labtop Znote 6214W with a core duo 2,16Ghz (T2600)...

I used the kernel 686 in order to use the multi-core functionality...

Fro the moment, i have only one issue with the CPU frequency scaling which is not working: when i tried to add the "CPU frequency monitor" applet, i got the following error:
CPU frequency scaling unsupported: You will not be able to modify ... or not have hardware support for CPU frequency scaling

Do i need to configure something to be able to manage the CPU frequency...

Thanks for your help

VF

---

### Post by djoelsson on 2006-07-21
Try adding "speedstep-centrino" to /etc/modules.
Worked for me!

Dan

---

### Post by vfanelia on 2006-07-21
Thks for the quick answer, i will try now...

---

### Post by vfanelia on 2006-07-21
I just did it and it's not working...

I really don't understand why the CPU is locked to the maximum frequency...   and i cannot change it using the CPU frequency monitor applet

VF

---

### Post by djoelsson on 2006-07-21
Don't take this the wrong way (I did this myself), but are you running on battery power?  If you're plugged in, your laptop might run at full speed all the time by default.

Also, add two copies of the cpu frequency scaling monitor to your panel so that you can monitor both cores.

Dan

---

### Post by vfanelia on 2006-07-21
> **djoelsson said:**
> Don't take this the wrong way (I did this myself), but are you running on battery power?  If you're plugged in, your laptop might run at full speed all the time by default.

Also, add two copies of the cpu frequency scaling monitor to your panel so that you can monitor both cores.

Dan
No, that's ok :smile: : you know i just want to understand why it is not working...
Well, i'm currently working on battery power and every time that i try to add the applet, i always have the same error message...
I added two instancies of the  cpu frequency scaling applet to monitor both cores but the frequency didn't changed (always the maximum value)

VF

---

### Post by djoelsson on 2006-07-23
I just thought of another thing.  Do you have powernowd installed?  If not, get it using synaptic.  That's the most important thing of all.  Without it, it definitely won't work.

Dan

---

### Post by vfanelia on 2006-07-24
> **djoelsson said:**
> I just thought of another thing.  Do you have powernowd installed?  If not, get it using synaptic.  That's the most important thing of all.  Without it, it definitely won't work.

Dan

I already installed it but every time i had the following message:
[B]
sudo apt-get install powernowd
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Les NOUVEAUX paquets suivants seront installés :
  powernowd
0 mis à jour, 1 nouvellement installés, 0 à enlever et 2 non mis à jour.
Il est nécessaire de prendre 0o/23,6ko dans les archives.
Après dépaquetage, 119ko d'espace disque supplémentaires seront utilisés.
Sélection du paquet powernowd précédemment désélectionné.
(Lecture de la base de données... 101092 fichiers et répertoires déjà installés.)
Dépaquetage de powernowd (à partir de .../powernowd_0.97-1ubuntu1_i386.deb) ...
Paramétrage de powernowd (0.97-1ubuntu1) ...
 * Starting powernowd...
 * CPU frequency scaling not supported                        
[ ok ]
[/B]

I really don't get it, i have a core duo which is normally using the speedstep technology...](*,) 

Well, i'm currently installing the suse 10.1 to check if it works: if it is the case, i will use it instead of ubuntu...

Too bad, i really like ubuntu...

Regards

VF

---

### Post by djoelsson on 2006-07-24
Hmm, it's really looking like it's a hardware problem.  Does it work in Windows?

Have you checked your bios to make sure your speedstepping is enabled?

After that, I'm completely out of ideas.  

Dan

---

