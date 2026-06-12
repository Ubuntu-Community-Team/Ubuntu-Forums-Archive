---
title: "Need deluge torrent"
date: 2008-09-21
forum: General Help
---

### Post by zohaib on 2008-09-21
Helo frndz., I have downloaded deluge torrent from here [http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php) but after downloading when i install it , it shows an error
here is the Error
when i double click on the deluge for installation it says in red words "Error: dependency is not setisfiable: labboost-date-time 1.34.1"

maybe I'm not using the supportable Installation file., 

Is anyone familiar with this problem?

and I need the link of deluge torrent which 100% works on ubuntu 7.04.

Thanks

---

### Post by Atsuko on 2008-09-21
Just do.
> sudo apt-get install deluge-torrent

---

### Post by zohaib on 2008-09-21
> **Atsuko said:**
> Just do.

when I past the value in terminal it ask for password n then after that it says ****"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package deluge-torrent is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package deluge-torrent has no installation candidate"****

any solution?

---

### Post by bingoUV on 2008-09-21
Search for "Add/Remove Software", or "Synaptic" in Applications menu. In this, there will be a search option. Search for deluge, and install it. 

Use these to install whatever software you need. You can search by name, or description.

---

### Post by GrandpaLeaman on 2008-09-21
Try installing from the repository. Go into System > Administration > Synaptic Package Manager and select Repositories in the settings menu. Then select the Third-Party Software tab. Hit the add button and put the following in the APT Line field:

deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) feisty main universe

Hit the add button then close. You will also need to reload. Then do a search for Deluge in Synaptic. Once you find it then you should be able to install it with all dependencies. I'm not absolutely sure this will work but it's worth a try.

---

### Post by zohaib on 2008-09-21
> **GrandpaLeaman said:**
> Try installing from the repository. Go into System > Administration > Synaptic Package Manager and select Repositories in the settings menu. Then select the Third-Party Software tab. Hit the add button and put the following in the APT Line field:

deb [http://ppa.launchpad.net/deluge-team/ubuntu](http://ppa.launchpad.net/deluge-team/ubuntu) feisty main universe

Hit the add button then close. You will also need to reload. Then do a search for Deluge in Synaptic. Once you find it then you should be able to install it with all dependencies. I'm not absolutely sure this will work but it's worth a try.

yea i did whatever u said but it didnt work for me., is there any other way?
btw thanks for the response friend n thanks for the response everyone., Appreciate that.

---

