---
title: "a few problems.."
date: 2008-05-20
forum: Hardware
---

### Post by ravelink69 on 2008-05-20
First. I have tried a few different things i have seen online and im not able to get it right. i have an HP Pavilion dv6000 and it has a nVidia 8400M GS (i believe its a GS) but anyways i cant seem to get it to work on a fresh copy of 7.10

any help would be appreciated

---

### Post by tamoneya on 2008-05-20
Saying "this doesnt work" makes it very hard for us to solve(althought we do love challenges).  It helps to have a little more information. what errors have you gotten? what exactly have you tried?  Where did it fail?

---

### Post by ravelink69 on 2008-05-20
i guess that would help....sorry im just a bit frustrated with something that i know is prolly only a small mistake on my part.

Basically i can get the video card to install.when i goto the restricted drivers management to enable the "NVIDIA accelerated graphics driver (latest cards)" then click enable i get an error :

The software source for the package
nvidia-glx-new
is not enabled.

---

### Post by tamoneya on 2008-05-20
go into terminal (applications -> accessories -> terminal) and type:```
sudo apt-get update
sudo apt-get install nvidia-glx-new
```

---

### Post by ravelink69 on 2008-05-20
```
Reading package list...Done
Building dependency tree
Reading state information...Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package nvidia-glx-new has no installation candidate
```

Thats what i get after entering the second code

---

### Post by tamoneya on 2008-05-20
try taking off the "-new" so it is just nvidia-glx

---

### Post by ravelink69 on 2008-05-20
hmmm still comes out the same :confused:

---

### Post by issih on 2008-05-20
Might be worth checking you have all the obvious repositories enabled in System->Preferences->Software Sources (I think that's the right location, I'm on the mac right now :))

Check that you have ticked to enable the universe and multiverse repositories, then try installing the package again

---

### Post by ravelink69 on 2008-05-20
i did that and it seemed to work, it installed nvidia-glx-legacy but we are back to my 2nd post, im still getting that error

---

### Post by ravelink69 on 2008-05-20
i was also told to try envy, when i go to install it i get a status msg : ERROR: Dependency is not satisfiable : debhelper

---

### Post by ravelink69 on 2008-05-20
now it says that it is inuse but if i try and enable it then it still gives me the error in my second post

---

### Post by werries on 2008-05-20
I'd watch out, the legacy version is meant for older cards. so unless you have an older card this is not meant for you.

So i suggest, removing that. and then trying to install the nvida-glx-new or nvidia-glx.

---

### Post by ravelink69 on 2008-05-21
would it be easier to upgrade to 8.04 and just worry about my wireless not working? i can get my nvidia card to work in 8.04 but i came back to 7.10 because it was easier to set up the wireless.

unless someone is able to help me with it now

---

### Post by ravelink69 on 2008-05-21
ok i have started the upgrade...i will just make a new post with the problems i have there

---

