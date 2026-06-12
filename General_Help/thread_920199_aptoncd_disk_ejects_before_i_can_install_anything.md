---
title: "aptoncd disk ejects before i can install anything"
date: 2008-09-15
forum: General Help
---

### Post by benner on 2008-09-15
i have xubuntu running. it is a remastered disk (remastersys) running on machines with no internet access. so i installed everything i wanted on another machine and then spun up a disk using aptoncd. when i put the disk in, i get a 'do you want to open the package manager' message, then the disk is automatically ejected.

it is crucial that i get this fixed ASAP. next sunday, i am going in to a school as a part of a charity project to install the OS on 30 machines then install the apps from the second cd.

i have 6 days to figure it out.

when i tried the disk on my regular system (ubuntu standard setup) the disk works normally so i know the disk isn't the problem.

---

### Post by benner on 2008-09-16
bump

---

### Post by gkestrel on 2008-09-18
On the machine that you want to install the packages on, do you have aptoncd installed ? if so use that to add the packages to the machine to be updated. If that fails you have other options you could use synaptic to add the cd, open synaptic and choose settings repositories to add your cd, this would require you to use the cd each time you wanted to install a package from it. Or you could use thunar with root priviledges by typing gksudo thunar into a terminal and copying all the deb packages from the cd to /var/cache/apt/archives 

I usually then do the following in a terminal

sudo apt-get update
sudo apt-get upgrade

hope this helps you out.

---

### Post by benner on 2008-09-19
thanks for the reply. 

as for your suggestions, i never get that far with the disk. i put it in, and it automatically opens a package manager (synaptic) then ejects the disk.

i am trying to test it out. i will be installing from the disk onto 30 machines with no internet access.

so far i can't get it.

i have remastered a new OS disk that has most of what i want on it so i may be able to get around the problem. for the future of our project though, it would be nice to get it to work.

or perhaps there is an alternative to aptoncd that does the same thing that i could try.

---

### Post by gkestrel on 2008-09-19
When synaptic has opened and the disk has been ejected have you tried closing the tray with the disk still in it and adding it to your repositories. Also when you get the message do you want to open the package manager, is there the oportunity to cancel it.

If all else fails how about on your first machine with all the updates installed, copy all the deb files from

/var/cache/apt/archives 

to a folder in your home folder and then just burn all the deb files to a new disk. You could then insert this disk into the other machines, cancelling any package manager messages, and finally copying all the deb files back to

/var/cache/apt/archives 

on the target machines by using thunar as root by entering in a terminal - gksudo thunar

---

### Post by benner on 2008-09-28
cancelling doesn't work. it just reopens again and again. i added the cd to the repoos. no difference. but your final suggestions could be how i ultimately have to do it if i find i need more packages. thank you. 

in the end, i have managed to remaster a different disk from the minimal install plus lxde and so i can get most of what i need on there without needing aptoncd. much smaller than using xubuntu as a starting point. the only stuff that doesn't fit is clipart and i can add that from a usb stick on most of the machines easily.

---

### Post by gkestrel on 2008-09-30
Only too glad to help, dont hesitate to post back if you have further problems.

---

