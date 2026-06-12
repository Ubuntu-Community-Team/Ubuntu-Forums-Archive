---
title: "[SOLVED] install lightzone"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by fingerrish on 2009-01-11
i wan't to install LightZone and i am starting to get mad with that terminal!!
in installation read-me there is said:
1.Open terminal as ROOT in this folder
[COLOR="Red"]what is ROOT?[/COLOR]
2.tar xzvf LightZone-3.5.tar.gz -C /opt
[COLOR="Red"]when i type this in, all i get is this:
tar: LightZone-3.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
[/COLOR]
i can't even get further with first step!
and the next steps are:
cd /opt/LightZone
sh LightZone
so help me - what i am doing wrong??

---

### Post by kranny on 2009-01-11
You need root permissions for that .
Just type```
 sudo tar -xvf lightzone.tar.gz
```
and copy it to the dir as it said

---

### Post by fingerrish on 2009-01-11
> **kranny said:**
> You need root permissions for that .
Just type```
 sudo tar -xvf lightzone.tar.gz
```
and copy it to the dir as it said
nop. still nothing happens - same thing

---

### Post by kranny on 2009-01-11
Where is the tar file stored.If it is on the Desktop first cd to Desktop

```
$ cd Desktop
$ tar xzvf LightZone-3.5.tar.gz -C /opt
```

---

### Post by fingerrish on 2009-01-11
> **kranny said:**
> Where is the tar file stored.If it is on the Desktop first cd to Desktop

```
$ cd Desktop
$ tar xzvf LightZone-3.5.tar.gz -C /opt
```

jes it is on desktop.
but still after these commands nothing changes.

---

### Post by jrusso2 on 2009-01-11
I think they want it to go into /opt so make sure you have that.  And move it there.

---

### Post by fingerrish on 2009-01-11
now everything is ok.
i did what kranny said - only needed to put sudo in-front of second line. installation is complete. thanks :)

---

### Post by lightbots on 2009-03-23
now that it is installed, how do you run lightzone?

---

### Post by tknudsen on 2013-01-18
type 

```
sh LightZone
```

to start the program, be sure to be inside the folder

---

### Post by CharlesA on 2013-01-18
Back to sleep you go...

---

