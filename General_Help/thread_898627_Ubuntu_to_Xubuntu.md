---
title: "Ubuntu to Xubuntu"
date: 2008-08-23
forum: General Help
---

### Post by metalmaniac248 on 2008-08-23
hi there


i am going to be getting a new desktop soon and will be using it as my main computer with ubuntu.

on my laptop which is currently my only pc, i have windows vista, and ubuntu. 

when i get the new pc i would like to keep windows on my laptop (for itunes only!!!!!) and replace ubuntu with xubuntu to gain a bit more speed as the laptop is not that good.

i have that there is a terminal command like "xubuntu-install" then "ubuntu-uninstall" that will chnage my ubuntu to xubuntu is this true

PS. i know those commands are probbably wrong :)



thanks

---

### Post by gjoellee on 2008-08-23
the code is:
```
sudo apt-get install xubuntu-desktop
```but using codes is the hard way!
[COLOR=Red][I][U][B]
I would recommend doing this one click install:[/B][/U][/I][/COLOR]
[apt://xubuntu-desktop](apt://xubuntu-desktop)

when finished log out and change session to "xubuntu" or "xfce"

---

### Post by LateNiteTV on 2008-08-23
cant you just install xfce?

---

### Post by sandysandy on 2008-08-23
see this

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

[http://www.linuxquestions.org/questions/ubuntu-63/migrate-from-ubuntu-to-xubuntu-456718/](http://www.linuxquestions.org/questions/ubuntu-63/migrate-from-ubuntu-to-xubuntu-456718/)

to quote above url
> If you ever think you want to remove it, install it with aptitude, not apt-get or Synaptic. 


regards

---

### Post by mb_webguy on 2008-08-23
> **sandysandy said:**
> see this

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

[http://www.linuxquestions.org/questions/ubuntu-63/migrate-from-ubuntu-to-xubuntu-456718/](http://www.linuxquestions.org/questions/ubuntu-63/migrate-from-ubuntu-to-xubuntu-456718/)

to quote above url



regards

That's a 2-year-old post.  Apt-get used to have problems with orphaned packages, which is why that post says to used aptitude.  But apt-get doesn't really have that problem anymore, and it's a bigger risk, in my opinion, to switch back and forth between aptitude and apt-get/Synaptic (and risk one not recognizing packages installed or removed with the other) than to use aptitude because it *might* be better at removing orphaned packages.

---

### Post by mrsteveman1 on 2008-08-23
> **mb_webguy said:**
> That's a 2-year-old post.  Apt-get used to have problems with orphaned packages, which is why that post says to used aptitude.  But apt-get doesn't really have that problem anymore, and it's a bigger risk, in my opinion, to switch back and forth between aptitude and apt-get/Synaptic (and risk one not recognizing packages installed or removed with the other) than to use aptitude because it *might* be better at removing orphaned packages.

Aren't they all just supposed to read the dpkg database to see what's installed? Or do they keep separate databases? 

I know on Suse the Zypper stuff seems to keep a separate database.

---

