---
title: "Error messege, openoffice.org-hyphenation-en-us!"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by ImbaDaimon on 2009-09-19
Recently i try to isntall OpenOffice 3.1 but somethink going wrong and now every time when i try to update my softwares i get an error messege window with **openoffice.org-hyphenation-en-us**.

I try this commands at terminal
```
sudo apt-get update
sudo apt-get upgrade
```

and get this messege

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up openoffice.org-hyphenation-en-us (2.4-2ubuntu1) ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postinst: 6: update-openoffice-dicts: not found
dpkg: error processing openoffice.org-hyphenation-en-us (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 openoffice.org-hyphenation-en-us
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

or

when i try to install somethink from Synaptic Package Manager i get this messege and at the end nothink is installed

[IMG]http://i238.photobucket.com/albums/ff27/ImbaDaimon/Varius/Screenshot.png[/IMG]

when i try yo uninstall this sh*t from Synaptic Package Manager i get this Error Messege

[IMG]http://i238.photobucket.com/albums/ff27/ImbaDaimon/Varius/Screenshot-1.png[/IMG]

I am new user of Linux and need your help with this problem. What is this? Why this happen? How i can solve it?

---

### Post by Hagar Delest on 2009-09-19
How have you installed from the repositories? or from the debs on OOo web site?

Try to remove that package alone.

---

### Post by ImbaDaimon on 2009-09-20
> **Hagar de l'Est said:**
> How have you installed from the repositories? or from the debs on OOo web site?

Try to remove that package alone.

From here :/

[http://ubuntuforums.org/showthread.php?t=1254544](http://ubuntuforums.org/showthread.php?t=1254544)

---

### Post by Hagar Delest on 2009-09-20
> **Hagar de l'Est said:**
> Try to remove that package alone.
Any change?

---

### Post by ImbaDaimon on 2009-09-22
Nope, when i try to remove it from Synaptic.. i get this messege..

[IMG]http://i238.photobucket.com/albums/ff27/ImbaDaimon/Varius/Screenshot.png[/IMG]

every time i am getting this messege... :/ i canot do anithink...

---

### Post by Hagar Delest on 2009-09-25
You should try the dpkg command line with the option to force a removal.

---

