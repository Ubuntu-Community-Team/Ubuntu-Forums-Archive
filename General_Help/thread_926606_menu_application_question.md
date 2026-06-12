---
title: "menu application question"
date: 2008-09-22
forum: General Help
---

### Post by guest_user on 2008-09-22
I'm using gnome and there's this firewall application, guarddog that I want to start using the menu with root privileges; as in I would like it to prompt me for the root password when I click on the menu option and give me the root rights to execute the application so I wouldn't have to go to the terminal and type in sudo guarddog, how would I go about implementing this function into the menu option?

i've tried changing the command of the menu option to sudo guarddog instead of guarddog but when I execute it, I don't get a prompt asking for my password.

---

### Post by annatar on 2008-09-22
Well...for getting a gui popup asking for your password
use 'gksudo guarddog' instead of 'sudo guarddog
 
sudo only works if you are typing the command in a terminal'

---

### Post by guest_user on 2008-09-22
ok thanks

---

