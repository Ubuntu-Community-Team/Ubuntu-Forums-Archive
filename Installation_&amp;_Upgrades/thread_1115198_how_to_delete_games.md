---
title: "how to delete games"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by kiridude on 2009-04-03
I want to delete all the pre-installed games that came with Ubuntu, but I am not sure what their names are. I already tried to delete with aptitude but the name was not recognized. Where can I find a list of all INSTALLED programs? I can only find all deb packages. 

I know its a simple procedure, but just need a few details.

Thanks

---

### Post by hakvoort on 2009-04-03
to remove the pre-installed games:

terminal -> sudo apt-get remove gnome-games gnome-games-data

that´s all :)

---

### Post by Pasdar on 2009-04-03
Click System > Administration > Synaptic Package Manager

In the quick search field type "game", and click on the first column, to show all the installed games at the top. < there is your list, now Right click on each one and click Mark for removal and then click Apply.

---

### Post by kiridude on 2009-04-04
Ok, thanks, got rid of the games, but does anyone know how I can get a list of ALL installed programs including those not in Synaptic? I would imagine they're all in a folder somewhere, just not sure which folder it is.

---

### Post by Ian Clark on 2010-01-25
It's weird but in Karmic, the command "sudo apt-get remove gnome-games gnome-games-data" does not work. I ran it and got:
```
Package gnome-games is not installed, so not removed
Package gnome-games-data is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
After reboot, the games are still there. I guess I'll try the Synaptic method next. Weird.

Edit: In synaptic, I found the package name is "gnome-games-common" now, so the command should be:
```
sudo apt-get remove gnome-games-common
```

---

### Post by sgosnell on 2010-01-25
```
dpkg --get-selections > ~/my-packages
```
will put the list of all installed packages into a file named my-packages in your home folder.

---

