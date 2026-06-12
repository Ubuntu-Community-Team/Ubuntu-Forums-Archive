---
title: "Where have all my programs gone?!"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Jerfo on 2009-10-30
Ok I just installed Karmic and I must have messed up something because all my programs are gone! Well, all those that are non installed alongside ubuntu, that is. Sure, it's not such a big deal since the stuff which can't be recovered is still there, it'll be just a matter of installing them but... wtf?! Or is there some weird thing that must be done? Funny thing is I still see the hidden files in my home folder for all my programs, they're just not there anymore, did they get overwritten somewhere along the installation process?

One thing does bother me, I used truecrypt and Alexandria before installation, is there anyway to recover access to my encrypted folders and the information saved with either of those?

---

### Post by LoloftheRings on 2009-10-30
How did you install these programs?

---

### Post by Jerfo on 2009-10-30
Well they were the programs I had installed throughout the year I've been using Ubuntu, the vast majority was installed using Synaptic or through terminal, a few through UbuntuTweak and a few others from lauchpad. Basically I am with a nearly fresh install of Ubuntu, for I found out earlier that also other stuff such as codecs are gone, it seems I'll have to install everything again.

---

### Post by hal10000 on 2009-10-30
> Ok I just installed Karmic and I must have messed up something because all my programs are gone!

If you did a fresh install, then it's no wonder that your previously installed programs are lost.

If you did an upgrade from jaunty, then some apps may have been removed caused by upgrade process. Your user-settings for these apps are still existing and you can reinstall them with apt-get or your package manager. But first take a look into your /etc/apt/sources.list because some of your repositories may have beeen commented out during the upgrade process.

---

### Post by Jerfo on 2009-10-30
Yeah that's what I thought... actually I found out after reinstalling emesene and screenlets that they worked just like before once reinstalled... oh well, thanks!

---

