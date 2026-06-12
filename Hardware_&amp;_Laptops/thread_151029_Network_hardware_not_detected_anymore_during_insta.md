---
title: "Network hardware not detected anymore during install, strange problem"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by miklp on 2006-03-27
Hi,
Here is a strange problem I have when I try to install Ubuntu 5.10 on my laptop. This makes that it's now almost impossible to install Ubuntu on it, although it's possible.

I began the install process of Ubuntu, my network hardware has been detected, and I could set up my internet connection : I had to choose between eth0 (ethernet) and eth1 (wireless), so I chose eth1, I entered my WEP key (however that is strange that I've not been prompt for my ESSID, as several networks are available in the surroundings), and it worked perfectly.
After that, I entered my hostname, and I let the default value (namely "ubuntu"). I pressed entered and then decided to go back (using Esc key) to choose a better hostname.
First minor problem : this step was not in the list of steps, so I decided to go back to the previous step namely "Detecting network hardware". Here it could not find again my connection.
So, I decided to reboot (Ctrl-Alt-Suppr), and to start again from the beginning. And now, my network hardware is never detected in the installation process !!!
I have the impression that only eth0 is detected since then, so I don't have the choice between eth0 and eth1 as the first time, and so the DHCP autoconfiguration doesn't work (and I'm never asked to choose eth1, and thus my ESSID and WEP key (as the 1st time for this one) neither).

So, I tried to reboot and start again a lot of times, and this didn't help ! Going back during the first installation (at a non-crucial step) broke the installation process ! ](*,)  That's very strange because nothing had been written on the disk during the installation process (I just did the 1st steps of installation).

I just want to say that I need the internet connection in the installation problems, because of Ubuntu issues concerning my X600 mobility graphic card. That's why I can't install Ubuntu now (at least in a simple way).

My question is : how can I do for "reinitializing" the installation process (reboot is not enough, I don't know why !) ?

---

