---
title: "where to find the sourcecode of an installed program?"
date: 2008-11-15
forum: General Help
---

### Post by bluppfisk on 2008-11-15
On my Ubuntu Intrepid installation, there are a few apps installed, such as Tetravex (gnotravex). However, there's a minor flaw in the application that I think I can fix on my own. So I decided to go and look for the sourcecode, but where can I find the sourcecode of gnotravex on my computer? Or is it in the repositories? How would I go about getting it?

Thanks

---

### Post by b0b138 on 2008-11-15
I believe using sudo apt-get source packagename will get the source. Just make sure the source repos are selected. All the default games are grouped together in the gnome-games package.

---

### Post by b0b138 on 2008-11-15
Just tried it with gedit, sudo apt-get source gedit worked. It downloads to your home folder

---

### Post by bluppfisk on 2008-11-15
sudo apt-get source gnotravex does not seem to work ):

---

### Post by mc4man on 2008-11-15
All the gnome games are in one package (gnome-games

So go (don't use sudo to get sources

```
apt-get source gnome-games
```


edit; if you can make your needed mods to the gnotravex source then just build off of the debian rules file and you'll get a proper gnome-games package you can reinstall from

---

