---
title: "quassel 0.3.0.1"
date: 2008-10-09
forum: General Help
---

### Post by Stargazer989 on 2008-10-09
i need help compiling Quassel 0.3.0.1. i can't get it to work for some reason. i do as it says but i get stuck on the 'make' part... what exactly do i type in after 'make' ?? if i type nothing then i get: make: *** No targets specified and no makefile found.  Stop.

anyone willing ?

---

### Post by Yellow Pasque on 2008-10-09
You didn't follow the directions in the INSTALL file, but you might not even need to build from source. If you're using Hardy, just enable the backports repo in (System -> Admin -> Software Sources) and there's a shiny quassel 0.3.0.x package waiting in the repo for you. :P

---

### Post by Stargazer989 on 2008-10-09
i added backports but it has last month's version (0.3.0) and i need to be using this month's version (0.3.0.1) cause last month's version has some weird bug. i click on a certain channel (#lobby of wonderlandIRC) and quassel just freezes with no debug output.

---

### Post by Yellow Pasque on 2008-10-09
Ok then, obtain the prerequisite dependencies:
```
sudo apt-get build-dep quassel
```
You need to create an empty build directory and then change to it and run cmake providing the path where you untarred the quassel source. Then you can make:
```
cd ~/
mkdir quassel-build
cd quassel-build
cmake </path/to>/quassel-0.3.0.1
make
```

---

### Post by Stargazer989 on 2008-10-10
> E: Unable to find a source package for quassel

:(

---

### Post by Yellow Pasque on 2008-10-10
You need to have the backports repo enabled when you do that.

---

### Post by Stargazer989 on 2008-10-10
i do have backports enabled.

---

### Post by Yellow Pasque on 2008-10-10
In the "Ubuntu Software" tab of that dialog, make sure you have "Source Code" checked.

---

### Post by Stargazer989 on 2008-10-10
it's working now. TY!~

---

### Post by Stargazer989 on 2008-10-10
ok... so i did 'make' ... it took about 5-10min... but where's quassel ? it's not in Applications > internet > quassel* ... and there's no bash command being found for it either. so...

---

### Post by Yellow Pasque on 2008-10-10
Excellent. I may play with this IRC client myself now that I have it built. :popcorn:

---

### Post by Stargazer989 on 2008-10-10
but erh.. how do i run it. :(

---

### Post by Yellow Pasque on 2008-10-10
```
cd ~/quasselbuild
./quasselclient
```
There should be an executable quasselclient file in the build directory. You can copy it to /usr/bin and make launchers for it.

---

