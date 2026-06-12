---
title: "HOWTO: add compiz kde or gnome or any desktop option to gdm or kdm"
date: 2008-09-07
forum: General Help
---

### Post by oobe-feisty on 2008-09-07
**Introduction**

This is for people who want to sometimes use compiz and sometimes not by easily selecting the desktop or wm in kde or gdm i.e gdm will have 2 options for gnome 1. gnome 2. gnome compiz. One advantage of this is that i find it integrates better with kde and gnome loading compiz at the beginning with out replacing kwin or naututils this prevents some oddities from occurring on startup such as icons not entering the tray icon.

**Assumptions**

You already have compiz working and use some kind of script that loads it 
when you start your desktop. i have provided a sample script that i use it works well with my nvidia card. you can use that script or the one you are already using would possibly be better.

**Before you Begin**

make sure you remove your old method of starting up compiz if you have it set to autostart in your desktop

**KDE 3.X**

make a script called startcompiz.sh

kdesu kate /usr/local/bin/startcompiz.sh

copy and paste the code below

```
#!/bin/bash
compiz  --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering


sleep 2
emerald --replace &


```

make sure the compiz line is all one line its hard for me to make it one line in this web based editor 

make a script called compizkde3 

kdesu kate /usr/local/bin/compizkde3 

then copy and paste the code below 

```
#!/bin/sh
export KDEWM="/usr/bin/startcompiz.sh"
exec /usr/bin/startkde
```


now make a file called kde3compiz.desktop

kdesu kate /usr/share/xsessions/kde3compiz.desktop

then copy and paste the code below 

```
[Desktop Entry]
Encoding=UTF-8
Name=Compiz KDE
Exec=/usr/local/bin/compizkde3
Icon=
Type=Application

```


thats it you should now have normal KDE and Compiz KDE as options in either kdm or gdm 

**Gnome**

make a script called startcompiz.sh

gksudo gedit /usr/local/bin/startcompiz.sh

copy and paste the code below

```
#!/bin/bash
compiz  --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering


sleep 2
emerald --replace &


```

make sure the compiz line is all one line its hard for me to make it one line in this web based editor 

make a script called compizgnome


gksudo gedit /usr/local/bin/compizgnome
 

then copy and paste the code below 

```
#!/bin/sh
export WINDOW_MANAGER="/usr/bin/startcompiz.sh"
exec /usr/bin/gnome-session
```


now make a file called gnomecompiz.desktop


gksudo gedit /usr/share/xsessions/gnomecompiz.desktop

then copy and paste the code below 

```
[Desktop Entry]
Encoding=UTF-8
Name=Compiz Gnome
Exec=/usr/local/bin/compizgnome
Icon=
Type=Application

```

thats it you should now have an option in gdm or kdm to start gnome with compiz or without

---

