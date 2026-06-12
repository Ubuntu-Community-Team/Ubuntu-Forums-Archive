---
title: "Not The ower on my 2nd hard drive"
date: 2008-08-05
forum: Hardware
---

### Post by TheMixtureMedia on 2008-08-05
Hi there I just did a new install for my 2nd hard drive and it says I am not the owner can someone please help me get my 2nd drive to know I am the owener please..........

---

### Post by doas777 on 2008-08-05
well i'm away from a linbox at teh sec, but I believe the answer you are looking for is in the umask parameter in your fstab.

if you open \etc\fstab you should see your partitions on the new hdd listed. you can set the umask=077 to give yourself (and only yourself) full control, or umask=000 to unrestrict it.

if your ownership problem is the filesystem, just use chown.

I wish I could go into more detail and give you some code, but I'm pretty tied up tonight.

good luck

---

### Post by TheMixtureMedia on 2008-08-06
> **doas777 said:**
> well i'm away from a linbox at teh sec, but I believe the answer you are looking for is in the umask parameter in your fstab.

if you open \etc\fstab you should see your partitions on the new hdd listed. you can set the umask=077 to give yourself (and only yourself) full control, or umask=000 to unrestrict it.

if your ownership problem is the filesystem, just use chown.

I wish I could go into more detail and give you some code, but I'm pretty tied up tonight.

good luck


I can not get Chown to work any help??

---

### Post by fuzzyk.k on 2008-08-06
chown -R {username} {full path}

for example to change ownership of everything inside /data to user test

chown -R test /data

---

### Post by TheMixtureMedia on 2008-08-06
chown: cannot read directory `/2ndharddrive/lost+found': Permission denied
chown: changing ownership of `/2ndharddrive': Operation not permitted


still will not let me

---

### Post by TheMixtureMedia on 2008-08-06
still can not figure it out anyone??

---

### Post by doas777 on 2008-08-06
> **TheMixtureMedia said:**
> chown: cannot read directory `/2ndharddrive/lost+found': Permission denied
chown: changing ownership of `/2ndharddrive': Operation not permitted


still will not let me


are you running these commands with 'sudo' ?

 ```
 sudo chown -r <user>:<group> <location> 
```

---

### Post by TheMixtureMedia on 2008-08-06
Hi i just tried it with sudo and got it to work thank you guys very much for all your help :-)

---

### Post by doas777 on 2008-08-06
glad it worked out for ya. 
be sure to mark the thread as solved, and good luck in all your future computing adventures.

---

### Post by Bios Element on 2008-08-26
> **doas777 said:**
> are you running these commands with 'sudo' ?

 ```
 sudo chown -r <user>:<group> <location> 
```

Only catch i found is it required a Capital "R" And not lowercase. Otherwise worked fine. Thanks for the tip. ^_^

---

