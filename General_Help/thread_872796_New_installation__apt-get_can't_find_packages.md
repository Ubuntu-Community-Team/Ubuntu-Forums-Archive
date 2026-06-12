---
title: "New installation:  apt-get can't find packages"
date: 2008-07-28
forum: General Help
---

### Post by rawlins02 on 2008-07-28
I recently installed  7.10 Gutsy Gibbon. When trying to install packages I'm getting error messages:

user@machine:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tcsh

user@machine:~$ sudo apt-get install nedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nedit

Update gives this:

user@machine:~$  sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done


I notice that all entries are commented out in  /etc/apt/sources.list

---

### Post by lordhaworth on 2008-07-28
are you definitely connected to the internet?

---

### Post by Potatoj316 on 2008-07-28
try ```
aptitude search SEARCHTERM
``` that will find packages that exist in your repositories.  You may have to enable other repositories for the packages you want.  Go to System->Administration->Sources (it might not be sources but its right next to synaptic package manager) and enable all the repositories there.  (you dont have to enable the source repositories)

now try your aptitude update and installs again.

edit: reading your post again it looks like your only checking the ubuntu CD for packages.  I would sugest enabling aditional repositories like it explained earlier.  (i think the menu option is "software sources")

---

### Post by Kevbert on 2008-07-28
It looks like a Software Source problem.  Go to System-Admin-Software Sources. Under the Ubuntu tab tick all boxes, untick the CDrom box.  Under Updates tick Important, Recommended and Unsupported boxes.  Close the window and in terminal enter
```
sudo apt-get update
sudo apt-get upgrade
```
Now you should be all to get that package providing its in the standard repositories.

---

### Post by Seisen on 2008-07-28
Post your source list 

```
cat /etc/apt/sources.list
```

---

### Post by dexter.deepak on 2008-07-28
> **rawlins02 said:**
> 
I notice that all entries are commented out in  /etc/apt/sources.list

simply uncomment the required repositories :) and 
```
sudo apt-get update
```

---

### Post by rawlins02 on 2008-07-28
Followed suggestions of Kevbert. Repositories now accessible.  Thanks to all for fast replies.

---

