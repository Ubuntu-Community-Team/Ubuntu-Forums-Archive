---
title: "diff between upgrade and fresh install?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by poldie on 2009-05-09
I installed 8.10 from scratch last year, and swore I'd do the same with 9.04, but it was too tempting to just upgrade, so I did.  To be honest, I've not noticed much of a difference, which I guess is a good thing.  I've read people recommending either the upgrade or a fresh install, but without giving any real reason.  What would I get for the few hours it would take me to back up stuff, do a fresh install then copy my stuff back, download/install apps etc?

---

### Post by zvacet on 2009-05-09
In general there is no difference at the end between upgrade and fresh install.Some people prefer fresh install because during upgrade errors are possible.In other hand others prefer upgrade via net.As I said before results are same.I do upgrade with alternate CD because I like to have CD if I need it.

---

### Post by lovinglinux on 2009-05-10
I don't have any reliable statistics, but it seems to me that most of the threads here about weird issues with 9.04 are from people who upgraded. Anyway, I think that the chance of encountering problems also depends on how you configured your stuff and how far you have messed with the system along the release cycle. A fresh install will avoid being affected by bad configurations and software that no longer work nice with the new release. 

For example, I did a fresh install because I was using Hardy Heron. I didn't want to upgrade to 8.10 then to 9.04. Additionally, Hardy was my first Ubuntu since I switched from Windows, so I imagined that I might have screwed some things during my first months learning the OS. Nevertheless, I did re-installed all my personal applications using a script generated on Hardy. Along with them, Python 2.5 was installed side by side with Python 2.6, because three of my personal programs depended on it. After are while using Jaunty, I realized that Python 2.5 was causing a lot of CPU usage and it was no longer necessary, due to Python 2.6 presence. The only applications still dependent on Python 2.5 were guake, mimms and ontv. So I removed those applications and Python 2.5. Since then, my system is much more responsive and the CPU usage is way below.

BTW, to download and install all your applications on a fresh installation, use this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

### Post by GregDT on 2009-05-10
I've never managed to do a successful upgrade. Every time I end up with screen lockups and general OS misbehaving. So I always do a fresh install. That being said the 9.04 fresh install has also been a disaster with persistent screen locks. This may be down to my personal hardware set up although I've seen a few other posters comment about this problem. 

So for now I'm sticking with 8.10.

---

