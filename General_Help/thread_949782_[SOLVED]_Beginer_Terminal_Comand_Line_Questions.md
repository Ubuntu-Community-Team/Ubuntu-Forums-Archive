---
title: "[SOLVED] Beginer Terminal/ Comand Line Questions"
date: 2008-10-16
forum: General Help
---

### Post by concerto on 2008-10-16
I want to play around with the terminal and learn a little about the command line.


Question 1.
When I first installed Ubuntu it made me set up a user name and password.
Is this user name automatically the "ROOT" or "Super User"?  Do I need to make up another user name and password before I start to play?  I don't want to mess anything up.


Do you guys know of any good how to terminal or command line web sites for beginners? 

Thanks for all your help.

---

### Post by Sam on 2008-10-16
About root: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Command line tutorial: [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by concerto on 2008-10-16
Thanks Sam

This is going to make me look really stupid butt... I don't know if I get it.

I just read what you sent me  "About root: https://help.ubuntu.com/community/RootSudo"

So the super user is called root on the terminal?
so on the command line it will say root instead of my name@computer name if I'm logged on as root?

So as long as it says my name @ computer i am not logged on as root?

---

### Post by Sam on 2008-10-16
> **concerto said:**
> So the super user is called root on the terminal?
so on the command line it will say root instead of my name@computer name if I'm logged on as root?

So as long as it says my name @ computer i am not logged on as root?

Exactly.

---

### Post by concerto on 2008-10-16
Awesome! thats what I needed to know.

Thank you Sam

---

### Post by Uprightcarrion on 2009-08-08
Hey I'm totally new to ubuntu so I'm learning how to use the terminal however I ran into a snag doing the 1st part of a tutorial I'm doing.
   
   When I use the cmd cd to change directories in can do it fine when files don't contain a space. How do I do it when a file does contain a space? i.e. a folder named "Snes Roms"

P.S. I'm running Ubuntu 9.04 if that makes a difference.

---

### Post by asmoore82 on 2009-08-08
> **Uprightcarrion said:**
> Hey I'm totally new to ubuntu so I'm learning how to use the terminal however I ran into a snag doing the 1st part of a tutorial I'm doing.
   
   When I use the cmd cd to change directories in can do it fine when files don't contain a space. How do I do it when a file does contain a space? i.e. a folder names "Snes Roms"

P.S. I'm running Ubuntu 9.04 if that makes a difference.

either use quotes, or "protect" the space from being "eaten" by the shell with a backslash:
```
echo "like this"
echo or\ this
```

---

### Post by Uprightcarrion on 2009-08-08
Thank you for your help I got it now :)

---

### Post by Uprightcarrion on 2009-08-08
How do i access say a mounted object such as a 2nd partition, usb stick or external HD?

---

### Post by Uprightcarrion on 2009-08-08
Never mind I found it thank you

---

