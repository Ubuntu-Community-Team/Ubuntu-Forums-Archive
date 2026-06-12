---
title: "Could not mark all packages for installation or upgrade"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by kjamo36 on 2008-12-29
Ok, i think i did something stupid... I ran a program called cruft removers and it removed deb packages for skype and virtualbox.. now i cant run those programs lol.

So im trying to reinstall it through synaptic package manager and it says
--------------------------------------------------------------------------------
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

virtualbox-2.0:

Package virtualbox-2.0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsolete or is not available with the contents of sources.list
--------------------------------------------------------------------------------
and i got the same message for skype.....


I need help..

---

### Post by Partyboi2 on 2008-12-29
Virtualbox 2.0 is not in the ubuntu repos, go [[COLOR=Blue]here[/COLOR]]("http://www.virtualbox.org/wiki/Linux_Downloads") and download the deb and install it.

---

### Post by cariboo on 2008-12-29
You must be behind on your updates, as the cruft remover was removed just before Intrepid went final.

Jim

---

### Post by kjamo36 on 2008-12-29
nice... i downloaded th Vbox deb and its working... small problem.

i have launcher in my cario dock with a " ? " as the icon.. and it works fine but im trying to get the vbox icon back for cario and i dont have a icon for the menu launcher

and finally i cant run it from run application.... this is a mess

---

### Post by kjamo36 on 2008-12-29
i update all the time, last time i updated was lastnight

---

### Post by Partyboi2 on 2008-12-29
You should find a vbox icon in /usr/share/pixmaps/VBox.png
You should be able to right click on the dock and "Add a manual launcher" and choose the  /usr/share/pixmaps/VBox.png for the image name or path. If you don't have a icon for vbox at that location do a google search for a vbox icon and download it and use it.

---

### Post by kjamo36 on 2008-12-30
ok cool i got vbox working great thanx.. but i tried to get the deb for skype marked "skype-debian_2.0.0.72-1_i386.deb" 

it opens with package installer but the status reads wrong architecture "i386"
I guess its because im running amd64

Is there a way to get it back in synaptic P. manager for download remove ect?

Linux is hard =s

---

### Post by Partyboi2 on 2009-01-01
You can add medibuntu to your sources and install skype
Open a terminal and for intrepid type
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
Or for hardy
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then add the key
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
``` then install the package
```
sudo apt-get install skype
```

---

