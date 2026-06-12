---
title: "Why wil this not work ?"
date: 2005-11-13
forum: General Help
---

### Post by audun1 on 2005-11-13
Hi. I have installed Ubuntu on my old compaq but i only get terminal.

My machine:
332mhz
208mb ram
160GB hd 
CD burner.
Network card. 

How can i start Gnome ?

Thanks .

---

### Post by foolsh on 2005-11-13
did you use a server instal?"type server"
or did you use the desktop installation "just hit enter"
try typing "startx" at the prompt and tell us what happens

---

### Post by audun1 on 2005-11-14
When I write startx i get this error:

bash: startx: command not found..

---

### Post by lisje on 2005-11-14
[QUOTE=audun1]When I write startx i get this error:

bash: startx: command not found..[/QUOTE]

did you sudo? you might want to install xorg if he still says that the command is not found... or install gnome by this command:

sudo apt-get install gnome

or

sudo apt-get install xorg

the commands might differ.. I can't check it now because I'm not on my ubuntu-box right now..

you can search with:

sudo apt-cache search xorg

greets,
Lisje

---

### Post by audun1 on 2005-11-14
Huumm i get the error:

Cant find package. 

it cant find gnome or xorg so i dont now what to do...

---

### Post by Pablo_Escobar on 2005-11-14
It should be:
sudo apt-get install gnome-desktop-environment
sudo apt-get install gdm

I hope it'll help.

---

### Post by az on 2005-11-14
Actually, try
sudo apt-get install ubuntu-desktop

 if you want to have a complete ubuntu system that works.



What probably happened is that the installation was not able to complete and you do not have a properly set up system.

If you get errors with the above command, check the integrity of your install cd.

---

