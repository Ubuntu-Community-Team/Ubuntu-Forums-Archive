---
title: "Sound muted on Dell inspiron"
date: 2010-05-21
forum: Hardware
---

### Post by manward on 2010-05-21
hi 

i was installed Ubuntu 10.04 two weeks ago and anything worked correctly.but today 

sound applet [on top panel] show muted icon although on sound preferences window all

channels up.i install alsamixer also and it channels are up also ?!

any suggestion ? 


thanks

---

### Post by manward on 2010-05-21
More info :

yesterday i installed alsa-drive-linuxant for modem, after this sound is mute and not 

work.now i delete alsa-drive-linuxant.but how test alsa driver or reinstall it ? 


plz help me.

---

### Post by CSInDevelopment on 2010-05-21
the inspiron 1750 64-bit? (thats the system I have and didnt have any problems, but volume icon often disapears so often need to run alsamixer)
if its another laptop then it could be a missing or dodgy driver?
try running ```

alsamixer -V playback

```
 to make sure it was the right part you were changing the volume of (I made that mistake on ubuntu 8.04, ended up the default was wrong)

---

### Post by droadtrip on 2010-05-21
[FONT=Impact][SIZE=2][COLOR=DarkRed]The same issue happened with my sound on my Dell Studio Laptop in Ubuntu 9.10. So I upgraded to 10.04. Sound worked, but not through the headphone jacks. Was told there was a bug fix out there for that. It seems working on the bug is affecting your Inspiron. I hope it gets fixed soon. The sound is fine on my other PC, Lenovo. [/COLOR][/SIZE][/FONT]

---

### Post by CSInDevelopment on 2010-05-21
> **droadtrip said:**
> [FONT=Impact][SIZE=2][COLOR=DarkRed]The same issue happened with my sound on my Dell Studio Laptop in Ubuntu 9.10. So I upgraded to 10.04. Sound worked, but not through the headphone jacks. Was told there was a bug fix out there for that. It seems working on the bug is affecting your Inspiron. I hope it gets fixed soon. The sound is fine on my other PC, Lenovo. [/COLOR][/SIZE][/FONT]

I installed 9.10 beta and had no issues of that on this inspiron
if you wanted to try to reinstall alsamaixer:
```

sudo apt-get remove alsamixer && sudo apt-get install alsamixer

```
should only install if removal worked...if the package name is different just modify it I cant remember personally what it is called as upgrading all software was enough to fix it for me

---

### Post by manward on 2010-05-21
thanks for your reply.but when i installed Ubuntu 10.04 for first time don't problem with sound and it work correctly also on Ubuntu 9.10 . [i have a Dell inspiron 1300]

when i run this command : 

sudo apt-get install alsamixer

result :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer


and when run this command :

sudo aplay -l

result : 

aplay: device_list:223: no soundcards found...


?!

this problem when occur that i install alsa-linuxant-driver for modem !!!

---

### Post by manward on 2010-05-21
can i repair ubuntu with cd for fix sound issue ?

---

