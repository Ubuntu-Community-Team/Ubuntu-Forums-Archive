---
title: "installing and using wine"
date: 2008-08-01
forum: General Help
---

### Post by apdc on 2008-08-01
I am very new to linux and xUbuntu.  I am trying to install and use Wine so that I can use a free to air satellite programmer for my receiver.  I understand that windows applications can be installed on linux with the help of Wine.  I have downloaded and extracted the wine directory to my desktop but can't figure out how to install it.  The readme text leads me to Tools and wineinstall, but when I double click or right click nothing seems to happen.

Please help?:)

---

### Post by Choad on 2008-08-01
in ubuntu, most programs are installed using the package manager "apt"

there are a couple of graphical "front ends" to apt, one is found in applications > add/remove, the other is found in system > administration > synaptic package manager

not sure if xubuntu is different here.

anyway, the easiest way for me to explain it over the internet (without being there in person to tell you what to click on) is to give you a command to execute on the command line

sudo apt-get install wine

if you type that in to a command line, it will fetch and install wine for you.

---

### Post by apdc on 2008-08-01
Thanks very much.  Where can i find the command line?

---

### Post by buzzmandt on 2008-08-01
also keep in mind wine helps run ***_some_*** windows programs in linux and is kind of hit and miss, what works on mine won't necessarily work on yours.  Go to [http://www.winehq.org](http://www.winehq.org) , follow the download link and follow the ubuntu instructions for which version of xubuntu you have (hardy, gutsy, etc).

---

### Post by dje on 2008-08-01
> **apdc said:**
> Thanks very much.  Where can i find the command line?

Applications >> Accessories >> Terminal ;)
Also read what buzzmandt has posted above, it is very useful information

dje

---

### Post by Choad on 2008-08-01
> **apdc said:**
> Thanks very much.  Where can i find the command line?
in ubuntu it is in applications > accessories > terminal

in xubuntu it could be called "command line" "terminal" or "shell" (it goes by many names) i am not sure which, but i am sure you'll find it if you look through the menu

---

### Post by buzzmandt on 2008-08-01
> **apdc said:**
> Thanks very much.  Where can i find the command line?
can't remember specifically in xubuntu but look for something called "terminal".  It's command line similar to DOS command line.

Edit:  thanks choad, beat me to it and with better detail

---

### Post by anewguy on 2008-08-10
The following link shows how to get to the terminal/command line in different flavors of Ubuntu:

[http://www.psychocats.net/ubuntu/terminal]("http://www.psychocats.net/ubuntu/terminal")

This includes Gnome, KDE and XFCe (xubuntu).

---

### Post by gjoellee on 2008-08-10
install WINE by clicking on the link below:
[apt://wine](apt://wine)

---

### Post by anewguy on 2008-08-11
I am not the expert here to post the exact notation, but perhaps someone can also post here the apt-get line to show how to be sure you are getting all of the dependencies as well.  While this user was dealing with wine, the same techniques apply to everything.  :)

---

### Post by Archimedes0212 on 2008-08-11
pretty sure it's just

sudo apt-get install wine

---

