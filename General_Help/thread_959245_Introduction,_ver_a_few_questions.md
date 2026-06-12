---
title: "Introduction, ver a few questions"
date: 2008-10-26
forum: General Help
---

### Post by RyanTO on 2008-10-26
Alright, so as you may have guessed from my username, I'm ryan . . I have only ever used Windows but i really wanted to give linux a try a guy in my programming class had the Ubuntu 8.04 CD .. so i took it and installed it on my computer.

Honestly, I cant see much of a difference from windows except for the fact that it has two desktop spaces, and different commands .. 

anyways, i was wondering if anybody could give me a really short, quick, but informative tutorial on using the Terminal (command prompt) .. I was looking at a certain thread on this site and it tells me i have to go to the root etc etc .. how do i install programs? (i think you do that through terminal .. correct me if im wrong) .

thanks alot ladies and gents

cheers,
RyanTO

PS. I've been noticing that there are different versions (is that the correct word?) of ubuntu .. i have no clue whatsoever of which one i have but im assuming its GNOME (if that is in fact a version :S) because when i start up some games it will say 'Nibbles A worm game for GNOME' for example. thanks again

edit: dont know why the title has ver in it :S

---

### Post by kevstar31 on 2008-10-26
Open up the terminal and hit enter after typing commands. The **man** command give you information on how to use different commands. Try typing **man vi** and do the same for other commands you can find using **ls /usr/bin**. you can install programs form the terminal using **apt-get**. When they say you need to be root to run a command you need to type **sudo** before the command and enter your password, but be careful because these commands can damage you system.

---

### Post by senseijose on 2008-10-26
if you are a new user i would recomend to use siynatipc package manager that you can find at system administration or the add/remove in applications before you play with terminal.  you can really damage your system if you use terminal incorrectly.  go to the ubuntu forum site where you can find a lot of tutorial about terminal.

---

### Post by CatKiller on 2008-10-26
> **RyanTO said:**
> how do i install programs? (i think you do that through terminal .. correct me if im wrong) .

In general, you don't need to use the command line to install programs. Synaptic is a very powerful graphical program that will let you install the programs that you want. Or you can use the Add/Remove programs utility that will install some popular programs, and third-party "Partner" ones.

You will see many people give a command-line answer to requests for help for a variety of reasons. This does not mean that graphical ways of achieving the same result are not possible. A command can be quickly given, is easily copied-and-pasted, and is an unambiguous method that gives instant feedback.

If your cd says "Ubuntu" rather than, say, Kubuntu or Xubuntu, then you are using Gnome. The others use KDE or XFCE, respectively.

Welcome to the community.

---

