---
title: "Trying to install ati drivers correctly"
date: 2008-09-14
forum: General Help
---

### Post by artti on 2008-09-14
Hey!

I have problems installing proper ATI drivers. Installing drivers with envyng looks like doesn't changed anything. Then i have downloaded from ATI homepages ati-driver-installer-8-8-x86.x86_64.run. And looks like it doesn't work too. Then i've tried to use others tutorials. But still nothing good. And currenlty i'm so far that when running some programm via terminal it shows error: "No protocol specified error: cannot open display:"

So anykind of help? Please.

System: Ubuntu 8.04, ATI Radeon X1200

---

### Post by artti on 2008-09-14
Now after running ati-driver-installer-8-8-x86.x86_64.run and trying to installi ATI drivers. I restarted computer. Shows that it loads and then i get black screen. I dont want to make clean ubuntu install, because i have nowhere to backup my home folder. Currently i use Crunchbang live cd.

Still looking any help.

---

### Post by Neo_The_User on 2008-09-14
The only way to fix it less than 20 minutes would be to copy your home folder to a CD or flash drive and re-install ubuntu and never touch Envy.

What I would do without re-installing it:

EnvyNG for drivers is terrible. Envy is terrible in 8.04. Never touch Envy. Your drivers are completly screwed up right now. If you do not want to do a fresh install (which is the only easy way to do it in 20 minutes including drivers) then go into Envy and remove the drivers. Restart your computer. Erase anything that has to do with ATi in synaptic. Do a search for ATi and do a complete removal of all applications (accelerators, drivers, etc) and restart your computer. Now erase the xorg.conf file and restart your computer. download the ATi drivers from the website and install it.

---

### Post by Casper Hansen on 2008-09-14
> **Neo_The_User said:**
> The only way to fix it less than 20 minutes would be to copy your home folder to a CD or flash drive and re-install ubuntu and never touch Envy.

What I would do without re-installing it:

EnvyNG for drivers is terrible. Envy is terrible in 8.04. Never touch Envy. Your drivers are completly screwed up right now. If you do not want to do a fresh install (which is the only easy way to do it in 20 minutes including drivers) then go into Envy and remove the drivers. Restart your computer. Erase anything that has to do with ATi in synaptic. Do a search for ATi and do a complete removal of all applications (accelerators, drivers, etc) and restart your computer. Now erase the xorg.conf file and restart your computer. download the ATi drivers from the website and install it.

I disagree. I use EnvyNG on my PC. Never had problems.

---

### Post by Neo_The_User on 2008-09-14
I always had problems with Envy. I try avoiding all possible video packages from the repository as possible.

---

### Post by artti on 2008-09-14
> **Neo_The_User said:**
> The only way to fix it less than 20 minutes would be to copy your home folder to a CD or flash drive and re-install ubuntu and never touch Envy.


Hmm... maybe i should do that. Have start to backup things.

---

### Post by artti on 2008-09-15
Installed finally new Ubuntu. Made two partition. One i hope to make for home folder. Currenlty there's last Ubuntu. And what is great. Rythmbox works. Hurrey. I'm so happy. I hope to get another things work to.

---

### Post by artti on 2008-09-15
I installed ati-driver-installer-8-8-x86.x86_64.run and when i go to ATI Catalyst Control Center it says that no ATI graphic drivers is installed or not function properly.

---

### Post by artti on 2008-09-15
Huh... thanks to jim_p i got it finally work. Installed xorg_fglrx_drivers and then he gave me xorg.conf file.

---

