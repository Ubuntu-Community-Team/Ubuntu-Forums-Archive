---
title: "Screenlets Install Error"
date: 2008-09-27
forum: General Help
---

### Post by mwalimu54 on 2008-09-27
Hi, 

    I'm trying to install screenlets in Gutsy.  I've read a bunch of other posts but none of them seem to apply to me.  I've tried sudo apt-get install screenlets from the terminal and this is what I get

jason@jason-laptop:~$ sudo apt-get install screenlets
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package screenlets

    I've also tried from Synaptics Pkg Manager but the search for "screenlets" brings no results.  I do have the repositories enabled through Synaptics.  What am I doing incorrectly?

---

### Post by anotherdisciple on 2008-10-01
open a terminal (Applications > Accessories > Terminal) and type the following.

```
echo "deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use" | sudo tee -a /etc/apt/sources.list
```

I got this info from screenlets.org, so I trust this repository.

```
sudo aptitude update
```

```
sudo aptitude install screenlets
```

---

