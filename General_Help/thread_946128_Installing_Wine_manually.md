---
title: "Installing Wine manually"
date: 2008-10-13
forum: General Help
---

### Post by virus2 on 2008-10-13
Can anyone pls explain the procedure of installing wine manually on Kubuntu 7.04??
I mean downloading some sort of deb package and running the same using sudo command.
Pls dont suggest to use adept manager,as the size of the installation is very large and i have dial-up connection at my home.
Thanks..

---

### Post by knattlhuber on 2008-10-13
You can download the .deb package of Wine from their archive:
[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

Then, in a terminal do:
```
sudo dpkg -i wine.deb
```

---

### Post by virus2 on 2008-10-13
I have already tried that method,but it gives some errors on running with sudo command,some dependencies missing errors.I have Kubuntu at my home PC and will post the log in evening today when i go home.
Also,why does the adept manager shows the download size of the wine pacakge to somewhere around 40mb,whereas the deb package from archieve is only around 9mb.
Thanks for your reply buddy....

---

### Post by knattlhuber on 2008-10-13
This will download (but not install) the Wine package and its dependencies to /var/cache/apt/archives:

```
sudo apt-get install -d wine
```

As regards the size difference between Synaptic and the deb packages on the website... no idea

---

### Post by cyclobs on 2008-10-13
i've managed to compile wine.

it's pretty easy and straight forward, first thing i compiled i think.... >.<

---

### Post by virus2 on 2008-10-13
> **cyclobs said:**
> i've managed to compile wine.

it's pretty easy and straight forward, first thing i compiled i think.... >.<

I have never compiled anything from source.Can you explain me the step by step procedure for compiling the same.
Also,is this activity distro-specific???I mean whether there are separate source files for Fiesty,Hardy,etc..
If yes,pls suggest one for Kubuntu 7.0.4 Fiesty version.
Thanks..

---

### Post by knattlhuber on 2008-10-13
I would rather advise against compiling from source when a deb package is available. Programs compiled from source will not be registered in the Synaptic package database (unless you use *checkinstall*) and may be difficult to uninstall. Also, you have to manage package dependencies yourself. If you want to install Wine, go with the deb package.

---

### Post by Yellow Pasque on 2008-10-13
You should keep your Ubuntu install up to date if you want to use the latest software. Feisty has reached end-of-life status, so you're probably going to run into dependency problems whenever you try to install software.

---

### Post by geirha on 2008-10-13
The difference is probably that it also counts the dependancies of wine. I suggest you run the following command on the machine you intend on installing wine on:```
sudo aptitude install wine
``` Not to install wine on your slow connection, but to take a note of the other packages it needs to install. Ones you got that list, you can search and dowload them from [http://packages.ubuntu.com](http://packages.ubuntu.com) somewhere with a faster connection.

Ones you got all those packages, including wine, put them all in the same directory and run ```
sudo dpkg -i *.deb
``` dpkg will sort out which order they need to be installed in, and install them.

---

