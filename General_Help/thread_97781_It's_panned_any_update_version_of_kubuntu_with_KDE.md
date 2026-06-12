---
title: "It's panned any update version of kubuntu with KDE 3.5?"
date: 2005-12-01
forum: General Help
---

### Post by JuanC on 2005-12-01
I think could be a good idea to make a CD with the same version of Kubuntu 5.10 only update KDE 3.4.3 to 3.5 , called for example , Kubuntu 5.10.1.

Them you can install a fresh Kubuntu 5.10 with KDE 3.5.

I don't want to take a risk installing a dapper alpha only to get KDE 3.5 , i know that you can update Kubuntu 5.10 over internet to get KDE 3.5 but it is easier to install in others PCs if you can install all over CD.

---

### Post by i_m_fletcher on 2005-12-01
You could always burn the .deb's for KDE 3.5 from synaptic's cache and then add that CD as a repository on the other computers.  If it's that important to you.

---

### Post by mlomker on 2005-12-01
There are ways to do network installs that pull all of the packages from the Internet rather than using a CD at all.  If you have a fast connection it's worth the trouble because you get all of the latest packages in the first place.

I'm a network admin, so I actually went so far as to set up my own mirror of the Ubuntu repos at work...I can install a new Ubuntu/Kubuntu machine pretty quickly over the LAN.

---

### Post by skyboy on 2005-12-02
hey, how do you actually setup your own mirror ??

---

### Post by mlomker on 2005-12-02
[QUOTE=skyboy]hey, how do you actually setup your own mirror ??[/QUOTE]

You use rsync.  There are some [docs here.]("http://www.ubuntulinux.org/download/mirror")  I created some filters so it'll only mirror the i386 binary files.  If you grab the whole works then it's over 100 GB.

---

### Post by skyboy on 2005-12-04
[QUOTE=mlomker]You use rsync.  There are some [docs here.]("http://www.ubuntulinux.org/download/mirror")  I created some filters so it'll only mirror the i386 binary files.  If you grab the whole works then it's over 100 GB.[/QUOTE]

Thanks for the info mate ;)

---

