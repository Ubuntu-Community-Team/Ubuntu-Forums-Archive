---
title: "How do I put a password on opening txt files?"
date: 2008-11-11
forum: General Help
---

### Post by RonB123123 on 2008-11-11
How do I put a password on opening txt files?

My computer is also used by a few of my friends every now and then. How can I place a password on opening certain files? I would rather do this than hiding the file because I want to keep my shortcuts on the desktop. :)

---

### Post by tbielawa on 2008-11-11
One way to get the result you are looking for would be to zip the files up and set a password on the files.

For example:

Right click a random text file you have
Select "Create archive..."
Choose a file extension like ".zip" that supports passwords
Click the "Other Options" button and then put in a password.


Or you could always just make them use a guest account on your computer while you password your entire account :)

---

### Post by RonB123123 on 2008-11-17
I was hoping for a way to password protect files by setting them up as only root could open them. And if you were to double click on it, just to open it, it would prompt you for a password just like if you tried to update your system using the Update Manager.

---

### Post by Marcus Derekus on 2008-11-17
right-click on the file select **properties>permissions** and then change permisions

---

### Post by oldos2er on 2008-11-18
You could use ccrypt.

---

### Post by Th3Professor on 2008-11-18
or gpg ;)

---

### Post by bodhi.zazen on 2008-11-18
As of 8.10 users have a private encrypted directory :

[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Individual files are not "password protected" in Linux as in general access is controlled by permissions. It may not sound like much, but other users can not see your information if you do not give them permission.

[uhelp]community/FilePermissions[/uhelp]

Although you can add a password to an archive , it is not as secure as encryption and passwords on archives are easily cracked / circumvented.

---

### Post by easoukenka on 2008-11-18
I would recommend making a folder you plan on putting all of your password protected files in then right click it set permissions for only root now on your desktop.  Then create a new shortcut on your desktop and for the command type gksudo nautilus ~/Desktop/yourfolder  

This will popup the box you asked for when you click on the folder then you can view all files and you will not need to edit every file in the folder with special permissions.

---

### Post by Th3Professor on 2008-11-18
Several people have mentioned it, though "permissions" is perhaps the best option. It's quick and easy.

---

### Post by RonB123123 on 2008-11-27
I think I'll just use the permissions method. Thanks everone!

---

### Post by binbash on 2008-11-27
make an encrypted directory via truecrypt and put your stuff there.

---

### Post by Th3Professor on 2008-11-27
You can also increase security with chmod, chown, etc., in any case, have fun. :) Securing data on a computer is very important.

---

