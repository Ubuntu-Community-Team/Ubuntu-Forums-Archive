---
title: "svn (a Tortoise like) How To"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by sam1948 on 2009-11-12
Well obviously command line (: 

```

sudo aptitude install nautilus-script-collection-svn nautilus-script-manager subversion zenity

```

```
nautilus-script-manager enable Subversion
```

u can add one more script for [_[COLOR="Blue"]creating repository[/COLOR]_]("http://ubuntuforums.org/attachment.php?attachmentid=180277&d=1294305856"),
download, unpack and save it under:
/home/$USER/.gnome2/nautilus-scripts/
```

sudo chmod +x /home/$USER/.gnome2/nautilus-scripts/Create_Repository

```
repository settings, users and so on must be set manually in the repository config files.


thats all.
worked on ubuntu 9.04 & 10.10, should work for any gnome based distro.(not the auto installation but the manual installation)
I haven't tried it yet.
enjoy

if u have an older any debian based distro try the following dont forget to find these packages {subversion, zenity} and install them.
manual installation:
download the [scripts]("http://ubuntuforums.org/attachment.php?attachmentid=135875&stc=1&d=1258012278") 
copy them into "/home/$USER/.gnome2/nautilus-scripts"
restart nautilus.
if it's not working go to the shell
```

sudo chmod -R +x /home/$USER/.gnome2/nautilus-scripts

```
restart nautilus again.


the menu should now be in the "mouse right button menu"

---

