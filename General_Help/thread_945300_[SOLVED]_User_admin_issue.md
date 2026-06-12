---
title: "[SOLVED] User admin issue"
date: 2008-10-12
forum: General Help
---

### Post by lemmy999 on 2008-10-12
I have just re-installed 8.04. Home is on a separate partition. I am trying to recreate the account for my wife who had an account previously. When I go System>Administration>Users and Groups it lists me but not her. When I try to add her as a user , using her old username and password I get an error message saying "Home directory already exists,please enter a different home directory path"

---

### Post by itix on 2008-10-13
Go to the terminal (apps => acessories => terminal) and type [COLOR="Green"]*sudo nautilus*[/COLOR]. Type your password (and never mind the fact that you don't get any stars, just type the password and press enter).

Back up your wife's documents => just save them in some folder somewhere, and remember to press [COLOR="Green"]*ctrl + H*[/COLOR], which will reveal hidden folders, while copying files from your wife's folder. Delete her old home folder, create her user again and just paste the backed up files in her new home folder.

---

### Post by lemmy999 on 2008-10-13
@ itix

Spot on mate!!

---

### Post by itix on 2008-10-13
I'll assume that means you got it solved. If so congrats, and make sure you mark the thread as solved ;)

---

