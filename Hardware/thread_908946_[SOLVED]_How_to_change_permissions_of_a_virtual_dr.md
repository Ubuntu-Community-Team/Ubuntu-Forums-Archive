---
title: "[SOLVED] How to change permissions of a virtual drive?"
date: 2008-09-03
forum: Hardware
---

### Post by Horacioklm on 2008-09-03
Hi, a new ubuntu user here. Here is the issue: i partitionated my hard disk so i got the ubuntu partition root (/) and another one for saving my files (the aim was to have a partition just for ubuntu and programs for it). I mounted that "virtual drive" in my user file /home/claudio/mexihcco (mexihcco is the name of the virtual drive). But i realized that i have no permissions for writting in mexihcco.

What can i do to change the permissions if the change options for that drive are unavailable (they are in a gray unaccesible color jeje)??
I tried using the terminal but i lack knowledge about commands to edit permissions from there.

I thank you in advance.

---

### Post by Horacioklm on 2008-09-03
I GOT IT!!, i changed the owner of the drive. In my case i used:

sudo chown -hR claudio /home/claudio/mexihcco

by that i can write on it and have complete power over it lol. 

Sorry but i really didnt know... i was lucky in google =P

---

