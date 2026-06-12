---
title: "ibooks and iproblims"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by montablac on 2006-02-17
ok,hi every one

im a new linux user,and ive mastered most of the basics of gnome and have tryed other X enviroments,none worked

any way

as you may have guesed this problim is for the 20 ibooks that are sitting at my school and just begging for ubuntu to be installed

so i did,but theres a snag

if i try installing 5.10,i get as far as the login screen and then nouthing

so i went a version lower,it dident seem to work at first,but then i tryed to do one at home where all the little kids diddent touch them,it worked,but again,with some snags

the first one is that i have to change my password,ON EVERY LOGIN!

this is a pain for the teachers and students alike,as itll get them confused

the second snag is that i can not run any adminastrative programs or the root terminal,this is bad because i need to remove anything thats even remotely intersting (tipical school pollicy,but i might keep a few games like abuse) and i need to install some cad software,maby a bit of science and english stuff as well if this takes off.but enough about that

when i try to run sometihing,im prompted for the password,i provide it then it pulled a windows and crashed with an eror "the child exited with a states of one" (or failed)

now you see my problim,any help,even if it only gets me one step closer to converting my school to linux,will be appreashed,but if you can find a walk through for powerpc ill send you a check for 10 NZD (roughely 7 cents american)

oh,and im on dial up as well,so dont pester me about trying kubuntu,cause unless they release it on a CD,im not spending 1 1/2 weeks DL it

and hi to all who bother reading this,and thanks

---

### Post by linear on 2006-02-17
Try 5.10 again, and after boot get to a shell (ctrl-opt-F1).
 
Edit /etc/X11/xorg.conf and comment out or delete the **load "dri"** line. <-- Oops. Ignore.
 
Restart Gnome: sudo /etc/init.d/gdm restart
 
EDIT: on second thought try **sudo dpkg-reconfigure xserver-xorg** first. Then restart Gnome.

---

### Post by aysiu on 2006-02-17
[QUOTE=montablac]
the first one is that i have to change my password,ON EVERY LOGIN!

this is a pain for the teachers and students alike,as itll get them confused[/QUOTE] What do you mean by you have to change your password on every login...?

---

### Post by montablac on 2006-02-17
[QUOTE=aysiu]What do you mean by you have to change your password on every login...?[/QUOTE]

i mean exactly what i said

when i go to login it sais
"you must change your password(root enforced)"

then im prompted for the old pass,and the new one twise,then i get the x screen

and as for that sudo thing,ill give it a try

---

### Post by montablac on 2006-02-18
this is just a simple bump,and a statement that im on dial up as well

---

