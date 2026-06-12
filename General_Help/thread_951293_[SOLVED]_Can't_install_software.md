---
title: "[SOLVED] Can't install software?"
date: 2008-10-18
forum: General Help
---

### Post by josemaster2228 on 2008-10-18
hey i have been having a little problem one day I log in into my Ubuntu and there is this little like stop sign that says something is wrong I click
licked on it and the update manager comes up and it says there is a problem I try to run synaptic but the same problem i try to use the add&remove same problem so now i can't install software or update my
Ubuntu so it says that i have to post this i don't know if you can help me because i need to install some software to convert some video files


'E:Problem parsing dependency Depends, E:Ocurrió un error mientras se procesaba btnx (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages, E:No se pudieron analizar o abrir las listas de paquetes o el archivo de estado.'

---

### Post by MaxIBoy on 2008-10-18
For the benefit of a great many people, could you translate that error message?

---

### Post by cariboo on 2008-10-18
See my post in this thread:

[http://ubuntuforums.org/showthread.php?t=951124](http://ubuntuforums.org/showthread.php?t=951124)

Jim

---

### Post by ajmorris on 2008-10-18
hi there,
can you please post the contents your /etc/apt/sources.list file and also, try running: ```
sudo dpkg-reconfigure --all
```

AJ

---

### Post by josemaster2228 on 2008-10-18
> **cariboo907 said:**
> See my post in this thread:

[http://ubuntuforums.org/showthread.php?t=951124](http://ubuntuforums.org/showthread.php?t=951124)

Jim

thanks a lot Jim now i know how to solve it but how do you exactly do it? sorry for the n00ness
:)

---

### Post by cariboo on 2008-10-18
Open up /etc/apt/sources.list in gedit, press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

Enter your password when aske. This will open /etc/apt/sources.list in a text editor to comment out a line put a **#** at the start of the line. To uncomment a line remove the **#** from the beginning of the line.

Jim

---

### Post by josemaster2228 on 2008-10-18
> **ajmorris said:**
> hi there,
can you please post the contents your /etc/apt/sources.list file and also, try running: ```
sudo dpkg-reconfigure --all
```

AJ

Thank you to a lot i hope the screen shot i attached does for the listing i it started doing some wired things and didn't help any i will try Jim suggested

---

### Post by Yellow Pasque on 2008-10-18
There is a "typo" in your source list:
```
gksudo gedit /etc/apt/sources.list
```
Change "harty" to "hardy". Save/close the file.

---

### Post by josemaster2228 on 2008-10-18
> **cariboo907 said:**
> Open up /etc/apt/sources.list in gedit, press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

Enter your password when aske. This will open /etc/apt/sources.list in a text editor to comment out a line put a **#** at the start of the line. To uncomment a line remove the **#** from the beginning of the line.

Jim

Done just one more question to make sure i don't mess up something i have uncommented the following, see the attachment. If i need to uncomment something else just tell me please

---

