---
title: "Botched upgrade, only partially installed"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Persephone66 on 2009-04-24
KDE does not fully load, at best I get a desktop with use of the mouse or keyboard. I tried to fix it in recovery mode by having it repair packages. in all the stuff that goes across the screen too fast for me to read all of, I see a lot of "cannot resolve address type errors. It does stop at a point to ask me if I want to continue with an upgrade of kdebase-runtime-data and an install of kdebase-data. it fails at the install with unmet dependancies and suggests running 'apt-get -f install' In trying that I get an error telling me 'E:Sub-process /usr/bin/dpkg returned an error code (1).' I'm also seeing errors that end in 'Broken pipe'.

I've also attempted 'apt-get upgrade' and I get errors telling me it cannot resolve the server addresses.

---

### Post by Persephone66 on 2009-04-24
Is there a way I can complete in the upgrade in text mode?

Starting with acquiring an ip address?

---

### Post by Persephone66 on 2009-04-25
Well I was able to figure out how to get an ip address and get the upgrade downloading. 

Hopefully it works.

---

### Post by Persephone66 on 2009-04-25
No such luck. :(

I get errors installing 'kdebase-data kdebase-runtime-data', 'kdebase-data', 'kdebase-runtime-data'

Subprocess killed by signal (broken pipe)
E: Subprocess /usr/bin/dpkg returned an error code (1)

I'm not sure where to go from here.

---

