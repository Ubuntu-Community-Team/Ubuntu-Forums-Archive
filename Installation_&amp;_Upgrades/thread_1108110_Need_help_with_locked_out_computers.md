---
title: "Need help with locked out computers"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by budfannan on 2009-03-27
I am not sure I am posting this in the right forum so please move if needed.

I work at a small non-profit Montessori School in Maine and we were given three computers running ubuntu. I have a reasonable knowledge of mac and windows but little experience with unix and nothing with ubuntu.  I am willing to learn and was given the task of running the system. 

My problem is that someone entered information at first boot up and created a password but does not know what it is.  They did this on two of the three comps. I have tried to figure this out but I do not know what it is. I also do not have discs I can reboot from.

Does anyone know how I can get around this password and then reset it.  

Thank you,
Ian

---

### Post by bapoumba on 2009-03-27
Boot in recovery mode, at grub menu (if the computer boots right into Ubuntu, hit escape, and you'll get the menu. Choose recovery).
Then, at the command line prompt:
```
adduser <choose a username here>
```
and give a password when prompted to. You will be asked for other infos, you do not have to give these if you do not feel like it.
Then:
```
adduser username admin
```
This will place you in the admin group with full sudo privilege.
```
reboot
```
and that should do it :)

Could you notify the person who gave the machines? It is not that convenient to give away computers without login infos..

You can download a Ubuntu CD here: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by budfannan on 2009-03-27
Thanks you for your response.  That worked wonderfully.  

Little clarification for you though.  It was a person here at the school who put in the password AND lost the start up discs.  The people who gave us the comps had nothing to do with it.

thanks again.
ian

---

### Post by bapoumba on 2009-03-27
Ah okay :)
Glad to see it's working now, enjoy Ubuntu and feel free to browse around and/or ask questions if you have any. Welcome!

---

### Post by JF_Sly on 2009-03-27
> **bapoumba said:**
> Boot in recovery mode, at grub menu (if the computer boots right into Ubuntu, hit escape, and you'll get the menu. Choose recovery).
Then, at the command line prompt:
```
adduser <choose a username here>
```
and give a password when prompted to. You will be asked for other infos, you do not have to give these if you do not feel like it.
Then:
```
adduser username admin
```
This will place you in the admin group with full sudo privilege.
```
reboot
```
and that should do it :)

Could you notify the person who gave the machines? It is not that convenient to give away computers without login infos..

You can download a Ubuntu CD here: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)


I have the same issue.  However when I try the above, all I get is an error message  "The User '<username>'  does not exist" and it will not let me create it.

Disregard my above comment....  I did not read the post correctly and missed a step.  When I re-read and followed correctly, I go in.

---

