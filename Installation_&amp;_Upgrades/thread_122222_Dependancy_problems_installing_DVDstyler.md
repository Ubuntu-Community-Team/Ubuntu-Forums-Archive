---
title: "Dependancy problems installing DVDstyler"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by Schmic on 2006-01-27
I am trying to install DVDstyler 1.4 on breezy and keep getting a configuration error saying :

```

checking for wx-config... no
configure: error:
        Please check that wx-config is in path, the directory
        where wxWidgets libraries are installed (returned by
        'wx-config --libs' command) is in LD_LIBRARY_PATH or
        equivalent variable and wxWidgets is version 2.4.2 or above.

```

I have tried to search to install it through apt-get or synaptic but cannot get it to work through that so i am trying to compile it myself, which way be dangerous considering my 2 weeks knowledge of linux:) 

I currently have wxWidgets 2.6.1.1.1ubuntu2, so i am guessing there is something i am missing that needs to be done. i went through and installed all that DVDstyler list as dependancies in there install file so i have reached a dead end.

If anyone can lend there experience to my problem it would be appreciated [-o<

---

### Post by Schmic on 2006-01-28
I have also been looking for other apps to create the menu's i want. Most of them seem to be KDE apps not Gnome apps which would prevent me from using them correct?

i have tried Qdvdauthor but it was not creating any scripts to run and i presume i would have to create the script myself which seems to defeat the purpose of having it in gui

anyone else have any other options i should try?

I just want to create menu's for my .mpg movies that i put on dvd.

---

### Post by Schmic on 2006-01-30
For anyone else comming upon this problem just add this to your sources.list

```
sudo gedit /etc/apt/sources.list
```

deb     [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu)                     breezy   universe
deb     [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/)     breezy   main

you can then install it by:

```
sudo apt-get update && sudo apt-get install dvdstyler
```

the only issue is that it will not be able to authenticate the dvdstyler install.

It worked for me \\:D/

---

### Post by loweb1 on 2006-02-07
Thanks, I was lost until I saw this post.

---

### Post by linear on 2006-02-07
[quote=Schmic]I am trying to install DVDstyler 1.4 on breezy and keep getting a configuration error saying :

```

checking for wx-config... no
configure: error:
        Please check that wx-config is in path, the directory
        where wxWidgets libraries are installed (returned by
        'wx-config --libs' command) is in LD_LIBRARY_PATH or
        equivalent variable and wxWidgets is version 2.4.2 or above.

``` 
[/quote] This is a bit late, but for anyone else trying to compile DVDstyler from source (say, for PPC):

The necessary library is **libwxgtk2.6-dev**.

---

