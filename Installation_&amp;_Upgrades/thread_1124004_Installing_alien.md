---
title: "Installing alien"
date: 2009-04-12
forum: Installation &amp; Upgrades
---

### Post by newcomer16 on 2009-04-12
Hi, 
I am a new user of ubuntu. i am having trouble installing alien.deb. i downloaded the package. to install it, i put the package in the current directrory then used **sudo apt-get install alien.deb**. The package was not installed and i just got error messages like ''E: Couldn't find package alien_8.69_all.13ubuntu_all''

I kindly request for any help on how to go about the installation of any downloaded deb package(with or without unfulfilled dependencies)

Thanks

---

### Post by tabibito on 2009-04-12
As I know apt-get is only to be used to install something from the repository. You should use dpkg to install from a .deb file. Try typing the following in your terminal:

```
sudo dpkg -i alien.deb
```

Alternatively, you could just double-click the .deb file to run it from GDebi package installer, you could also run the GDebi package installer from Applications-->System Tools menu and the open the .deb file from there.

---

### Post by jacksaff on 2009-04-12
You don't generally have to download packages independently in linux. Alien is in the repositories so

sudo apt-get install alien

If for some reason you need to download a version different to the one in the repo, then kubuntu has kde set up to just click the .deb and a dialog will pop up. I assume ubuntu has similar.

dpkg -i packagename 

will also install a .deb that you have downloaded.

---

### Post by newcomer16 on 2009-04-12
thanks friends.

---

