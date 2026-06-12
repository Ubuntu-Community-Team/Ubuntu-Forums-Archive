---
title: "Disable deb-src while preseed"
date: 2008-08-09
forum: General Help
---

### Post by creame on 2008-08-09
Hi all,

I am a newbie to Ubuntu and now trying to learn in and out of preseeding. I had stucked in few areas while preseeding.This is one among them. the problem is, i dont want to have deb-src lines in my newly installed client's /etc/apt/source.list. 

As i have a local update server i need only the following lines to be there in my newly installed client's source.list.

```
deb http://192.168.4.43/ubuntu hardy main restricted universe multiverse
deb http://192.168.4.43/ubuntu hardy-updates main restricted universe multiverse
deb http://192.168.4.43/ubuntu hardy-security main restricted universe multiverse
```

i am success in having these lines in source.list without any other default lines, but it is adding deb-src lines also for the above mentioned deb lines.

like;
```
deb http://192.168.4.43/ubuntu/ hardy main restricted
deb-src http://192.168.4.43/ubuntu/ hardy main restricted
deb http://192.168.4.43/ubuntu/ hardy-updates main restricted
deb-src http://192.168.4.43/ubuntu/ hardy-updates main restricted
deb http://192.168.4.43/ubuntu/ hardy universe
deb-src http://192.168.4.43/ubuntu/ hardy universe
deb http://192.168.4.43/ubuntu/ hardy-updates universe
deb-src http://192.168.4.43/ubuntu/ hardy-updates universe
deb http://192.168.4.43/ubuntu/ hardy multiverse
deb-src http://192.168.4.43/ubuntu/ hardy multiverse
deb http://192.168.4.43/ubuntu/ hardy-updates multiverse
deb-src http://192.168.4.43/ubuntu/ hardy-updates multiverse
deb http://192.168.4.43/ubuntu hardy-security main restricted universe multiverse
deb http://192.168.4.43/ubuntu hardy-security main restricted
deb-src http://192.168.4.43/ubuntu hardy-security main restricted
deb http://192.168.4.43/ubuntu hardy-security universe
deb-src http://192.168.4.43/ubuntu hardy-security universe
deb http://192.168.4.43/ubuntu hardy-security multiverse
deb-src http://192.168.4.43/ubuntu hardy-security multiverse
```

there u can see, that for each entry it automatically adds the deb-src lines, which actually i dont need.

i tried the following;

1. in preseed i put like this;
```
d-i apt-setup/local0/repository string \
 http://192.168.4.43/ubuntu hardy main restricted universe multiverse
d-i apt-setup/local0/repository string \
 http://192.168.4.43/ubuntu hardy-updates main restricted universe multiverse
d-i apt-setup/local0/repository string \
 http://192.168.4.43/ubuntu hardy-security main restricted universe multiverse
#d-i apt-setup/local0/comment string local server
# Enable deb-src lines
d-i apt-setup/local0/source boolean false

```


2. then i tried by commenting that line like;
#d-i apt-setup/local0/source boolean true


but both setting didnt worked for me.

NOTE: i know, i can do a preseed/late command to fetch my tailored source.list and copy to /etc/apt/. but thats not the way i want to do this, i need to do it within the preseed commands (especially bcoz, i have lot other things to do with the preseed/late command), and i feel like it will work but i am missing something in it.

hoping for the best;

Creame:)

---

### Post by creame on 2008-08-09
no one is there to help me???

---

### Post by creame on 2008-08-09
waiting for the last 7 hours...? now one der?????

---

### Post by dioktos on 2008-08-11
I have much the same question. I don't want any of the regular lines in sources.list to be uncommented, since my local repository mirror combines hardy, hardy-updates and hardy-security into a single distribution. The only lines I want enabled in my sources.list are the ones specified by  apt-setup/localX.

I can always copy a sources.list over in the post-installation script, but I feel confident there's a way to do it in the preseed file.

---

### Post by creame on 2008-08-12
nobody is der 2 help us????

---

