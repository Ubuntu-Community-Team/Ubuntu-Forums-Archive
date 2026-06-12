---
title: "Lacie Lightscribe help"
date: 2008-09-25
forum: General Help
---

### Post by Forbees on 2008-09-25
Hey guys, i've been using ubuntu for over a year now, started off with feisty, and you've all been such good help i've never had to make an account and ask for customized help

until now

i started off with the lightscribe software from the lightscribe web site, and it worked fine . . . it's just it only has lame text writing abilities. i contacted lightscribe and they recomended Lacie 4l

i've yet to get lacie working >,<

Problem 1: when trying to install the host software(after converting to a .deb with alien) i get an error saying a newer version is already installed. i figured that it might be the host software from lightscribes simple maker.

Problem 2: the actual software from lacie installed fine, but it doesn't detect my drive(lightscribes program did, and worked)

my attempt to fix:
 thinking that the lightscribe software was interfering with the lacie, i opened up a root window and started removing all lightscribe related objects( probably a horrible move, but i dont know how to uninstall w/o add/remove apps)

after removing anything and everything i could find to do with lightscribe i still get the same errors

i'm pretty sure i didn't miss any files during the removing, i opened up the package managers and double checked what files it put on there


so heres the thing. . . . . i'm a being a tard right now?

---

### Post by Infinite Indefinite on 2008-09-27
What make is your lightscribe drive - the one that wasn't being recognized?

(I can confirm that the LG GSA-E60L is recognized and works fine.)

---

### Post by Forbees on 2008-09-27
samsung something

---

### Post by catfishy on 2009-09-17
Hey there!  I have the same trouble with my drive... the "lame" text writing app works fine, but the lacie one with the nice picture-abilities doesn't recognize the drive.

---------------
[IMG]http://i26.tinypic.com/4i061f.png[/IMG]
---------------

Hmmm.... I've tried changing wine's cd-rom around but to no avail;
any suggestions?!
thanks!


FIGURED IT OUT:
```
sudo apt-get install libstdc++5
```
and then you have to have gksudo to start it:
```
gksudo 4L-gui
```

Worked for me... recognized the drive!

---

