---
title: "Dependancies problem"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by DShad on 2009-01-29
I installed latest mythtv from ppa (0.22) on my Ubuntu 8.10 but the installation was unable to complete because of this file:

nvidia-180-libvdpau

The reason could be because I am using nvidia version 177

The problem now is that I am not able to une apt-get upgrade anymore because it gives me a dependancy problem like this:

--------------------------
Vous pouvez lancer «*apt-get -f install*» pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites*:
  libmyth-0.22-0: Dépend: nvidia-180-libvdpau mais il n'est pas installé
E: Dépendances manquantes. Essayez d'utiliser l'option -f.
--------------------------------


Please help

---

### Post by abraxas334 on 2009-01-29
Did you try and do this? use the -f option?
> Essayez d'utiliser l'option -f.

other things to try maybe go into synaptic and do a repair?

or get the latest nvidia driver from the nvidia website and install that?

---

### Post by DShad on 2009-01-29
Yes I did try the -f option with no luck.

Also try a repair but didn't succeed.

I managed to get the latest drivers from Nvidia (.run) and would need a little help to install it (since it's not a .deb).

Any help appreciated

---

### Post by abraxas334 on 2009-01-29
Well there is another thread about this were this issue is being discussed they haven't come up with a solution yet, but think that uninstalling and reinstalling the drives was a bit extreme. I ended up having to do this as i couln't find another solution and my graphics weren't working at all. So not quite the same problem.
This is what i did to install the 180 driver from the website. 

[http://ubuntuforums.org/showthread.php?t=1053950]("http://ubuntuforums.org/showthread.php?t=1053950"),
 shouldn't take more than 15 mins to do, however i'd have alook around the forum for a bit longer and maybe wait for someone more knowledgable to comment on this. But i guess if all fails there is always this option.
Good luck with it.

---

