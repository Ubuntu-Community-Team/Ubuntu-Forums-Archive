---
title: "[SOLVED] Installing ubuntu"
date: 2008-09-20
forum: General Help
---

### Post by rasmus91 on 2008-09-20
Hi People

I just got a new laptop (dell Latitude E6400) i wanted to install ubuntu, so i tried to use the Wubi, but since it didn't work i tried installing as a program in windows. then, when i enter ubuntu i try to install ubuntu on a part of the harddrive, it only goes to the part where it scans the harddrive. then it comes up with something about, not being able to start.... (well i dont really remember what it is) it says that i could try to go on anyway, but it properly won't be able to properly install ubuntu. and if i want any more information about it i should be able to find it in /var/(something) well i entered the string, but wasn't able to see it. the console wrote: Accses Denied.

Any ideas on how to install? can i download a installer, to use from the ubuntu in windows? I hate vista even more now!!!!

---

### Post by wpshooter on 2008-09-20
Are you planning on continuing to use M/S Windows or do you want your machine to use ONLY Ubuntu ?

---

### Post by Dougie187 on 2008-09-20
First off, you really should find out what the error message it gave you was, because that's likely the only way people are going to be able to help you. In addition to that, to find the log file (the /var/whatever) its probably going to be a file in /var/log

Depending how you are trying to access that you will have issues, but you should be able to type one of these commands to access it.
Press Alt+F2 and type
```
gksudo gedit /var/log/**filename**
```

OR:
From a terminal type
```
sudo cat /var/log/**filename** > ~/Desktop/Logfile
```

Just replace filename with the correct file name in both of those. The terminal one will give you a file on your desktop called Logfile that will have to contents of the log file in it, and the other one will just open it up in a gui text editor. After you get the information people need to help, just post it here and people will see if they can help you.

---

### Post by rasmus91 on 2008-09-20
I'll try that :) ty...

btw, i wanna dualboot

---

### Post by rasmus91 on 2008-09-24
hey, never went that far to solve it. tried just to reinstall wubi, that did the job... :D

---

