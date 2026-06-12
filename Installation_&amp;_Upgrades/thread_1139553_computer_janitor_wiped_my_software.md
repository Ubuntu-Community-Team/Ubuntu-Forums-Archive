---
title: "computer janitor wiped my software"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by djbenny on 2009-04-27
hello

computer janitor did a cleanup now half my software has dissapeared, and some of it wont re-install... how can i rectify this.

ubuntu 9.04

---

### Post by kfchen on 2009-04-29
I have the same problem here. 
I removed the ubuntu-tweak and now have no way to re-install that. 
Help!!

---

### Post by Mark Phelps on 2009-04-29
> **djbenny said:**
> hello

computer janitor did a cleanup now half my software has dissapeared, and some of it wont re-install... how can i rectify this.

ubuntu 9.04
If you're looking for a one-click solution, not aware of any.

Basically, you'll have to use Add/Remove or Synaptic to install your apps again.  If the packages didn't get removed from the apt cache, you can simply reinstall them in synaptic; but if they did get removed, you'll have to download them again.

---

### Post by Mark Phelps on 2009-04-29
> **kfchen said:**
> I have the same problem here. 
I removed the ubuntu-tweak and now have no way to re-install that. 
Help!!

You can go to their website, download the .deb and reinstall it.  Or, you can use the info on their website to add a third-party repository to synaptic and add it that way.

---

### Post by rucci on 2009-05-13
Does the janitor write to a log listing what it removed?

---

### Post by jonobr on 2009-05-13
HEllo

Stupid question from jonobr, going back to the original action.
IS this a known issue with the janitor,
does anyone know why this happened?
I have not run janitor yet, but Im wondering how this has not been seen before

Thanks!

---

### Post by Mark Phelps on 2009-05-13
Don't know if this is a general problem with Computer Janitor, but I've followed a general practice of staying away from clean-up utilities unless they do something very specific.

On the MS windows side, I see this same problem when folks run some kind of registry cleaner only to reboot and have a bunch of their apps not work anymore or, in worst case, not even be able to boot properly.

It's also a good practice to back up your installation before you attempt something like this just in case it wipes more than you want.

I've seen this same kind of behaviour with the apt-get cleanup option. Tried it and Open Office wouldn't work anymore.  (Course, I had a backup to reload from and fix that).

---

### Post by lightstream on 2009-05-13
if you install so many crappy programs that you actually consider installing another crappy program to sort out the mess of crappy programs you've already installed, I really don't think there's much hope for you, sorry.

---

### Post by BobbyS on 2009-05-13
Wow.................a ray of sunshine!

---

