---
title: "kdm display manager kdm not running"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by senzacionale on 2005-11-13
i have some problems after each restart. I get this mesage.

kdm display manager: kdm not running (var/run/kdm.pid not found)

How to fix that!

---

### Post by tseliot on 2005-11-13
[QUOTE=senzacionale]i have some problems after each restart. I get this mesage.

kdm display manager: kdm not running (var/run/kdm.pid not found)

How to fix that![/QUOTE]

This might mean you are using GDM instead of KDM.

Is everything else ok? I mean, can you see the graphical interface?

---

### Post by senzacionale on 2005-11-13
yes i can see graphical interface and yes i am using gdm not kdm. So how i can remove this error message!

---

### Post by Teroedni on 2005-11-13
It is nothing to worry about
It just means that kdm wants to start but gdm wont let is;)

gdm is gnome graphics on the logon screen
kdm is kde graphics on the login screen

Thats the only difference
They do not do any thing else then give you the choice of which user and which 
wm you will run

wm=Window managers such as :kde gnome xfce windowmaker icewm etc

so if you want gdm to run at startup just remove kdm
if you want kdm just remove gdm;)

---

### Post by senzacionale on 2005-11-13
ok i want to run gdm not kdm so how i can delete kdm now. I try everything but i don't now how to make this. I also want to remove kde from my system but also don't know how?

Thnx

---

### Post by Teroedni on 2005-11-13
go into synaptic
or if you cant find snaptic write in terminal

sudo synaptic

the go to search in synaptic and search for kdm

right click on the text wher it stands kdm and mark for complete removal

---

