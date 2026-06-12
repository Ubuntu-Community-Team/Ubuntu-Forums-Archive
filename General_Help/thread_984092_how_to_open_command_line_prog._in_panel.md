---
title: "how to open command line prog. in panel"
date: 2008-11-16
forum: General Help
---

### Post by llew on 2008-11-16
I have a program (tobu)that opens in the command line:
$ cd tobu-0.5.2
$ python tobu.py
I want to run it from a panel button
how do I do it??
I know how to get an 'application launcher' to the panel but don't know how to script it!
help appreciated .
I'm using ubutu 8.04
llew

---

### Post by binbash on 2008-11-16
right click to panel,select add to panel , select custom application launcher.(select your icon name etc)

Then write to this to command section : 

cd && cd tobu-0.5.2 && python tobu.py

ps : cd will go to your home

---

### Post by llew on 2008-11-16
Many thanks for reply.

unfortunatly when I now click on button I get:

'Could not launch application
failed to execute child process "cd" (No such file or directory)'

this is what I cut&pasted in to 'command:''launcer propoties':
 cd && cd tobu-0.5.2 && python tobu.py
??????????????

---

### Post by binbash on 2008-11-16
remove cd &&

---

### Post by llew on 2008-11-16
modified as sujested but still get same error message as before?

---

### Post by binbash on 2008-11-16
python /home/blablablablalbla/aadsd/script.py

---

### Post by llew on 2008-11-16
thanks that last worked!
much appriciated.

---

