---
title: "how to change the user permission"
date: 2008-09-14
forum: General Help
---

### Post by francrouge on 2008-09-14
Hi Everyone [B][U]i'm new with ubuntu
[/U][/B]
I would like to copy a vlc theme in usr/share but when I copy my folder it says that I don't have the permission. 

can someone help me please

---

### Post by ju2wheels on 2008-09-14
You will need to know the exact location of the folder you are trying to copy. Unlike Windows you cant copy to a directory outside of your home folder without super user permission.

Open Applicaitons->Accessories->Terminal

Then do the following:

```

sudo cp -R /home/username/folderYouWantToCopy /usr/share/destinationFolder

```

---

### Post by francrouge on 2008-09-14
okay thanx its working but its a long processus for just a little transfere so I have an other question How I can a make my user to HAVE the FULL ACCES ON ANY FOLDER is it possbile sorry for maj

---

### Post by ju2wheels on 2008-09-14
This is a big security issue for Linux and this is why that is not possible without becoming a super user. What you are asking is essentially running as root, which I will not go into for your own security purposes. It may seem like a lot but this keeps you protected from viruses, trojans and other security vulnerabilities.

In addition, you will typically not need to do such copying to system folders unless you are modifying or installing a program or its settings.

---

### Post by sisco311 on 2008-09-14
You can run your file manager as root.

Press Alt+F2 and run:
```
gksu nautilus
```Be careful, as root you can do anything with every file and folder.

---

### Post by francrouge on 2008-09-14
okay thank you for your answers guys i'm really new to linux so I think I will wait a bit before do that but thx for your help people on linux forum are pretty fast compare to other OS Xd 

Francrouge

---

