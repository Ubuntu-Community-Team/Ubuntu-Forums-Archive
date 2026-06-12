---
title: "ATI drivers aren't working, freaking out"
date: 2010-05-30
forum: Hardware
---

### Post by TotempaaltJ on 2010-05-30
I'm using Ubuntu 10.04 with an ATI Radeon HD 4870. The drivers I got from the AMD site work, but I can't turn on any effects, compiz etc. I've googled for some time and found out I had to edit xorg.conf, which I did, but no change.

I'm completely lost, and I really hope that anyone could explain to me what I have to do to get the ATI drivers working!

---

### Post by proggy on 2010-05-30
Did you install the drivers after a fresh Ubuntu  install?

---

### Post by dE_logics on 2010-05-30
You need to manually configure the ATI drivers before they do their thing...so it was not a good idea to install manually, you could have got it from the repos, that configures automatically.

Now you have to remove these drivers first with - 

cd /usr/share/ati;./fglrx-uninstall.sh

Then install the fglrx drivers form synaptic.

---

### Post by TotempaaltJ on 2010-05-30
I just installed Ubuntu today. First my effects worked, than I saw I could install ATI drivers, so I did, than it didn't work. By then I'd guessed I'd f***ed up.

I uninstalled everything, and now nothing works. Ugh.

---

