---
title: "problem in update &amp; instalation of program"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by m3asmi on 2009-05-11
[FONT=Arial Narrow][SIZE=4]I have problem in update & installation of program from delete/add program 
I see this message: [/SIZE][/FONT]
[SIZE=5][COLOR=Red]
W: Échec de la récupération de [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.8-0ubuntu3.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs-data_3.5.8-0ubuntu3.1_all.deb)
  404 Not Found [IP : 91.189.88.140 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.8-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.8-0ubuntu1_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu11_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt-x11-free/libqt3-mt_3.3.8really3.3.7-0ubuntu11_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.8-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.8-0ubuntu1_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-qt3-1_0.6.20-2ubuntu3_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblua50_5.0.3-2build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblua50_5.0.3-2build1_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblualib50_5.0.3-2build1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lua50/liblualib50_5.0.3-2build1_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr2c2a_1.2.2-4.3ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr2c2a_1.2.2-4.3ubuntu2_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]


W: Échec de la récupération de [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.8-0ubuntu3.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdelibs/kdelibs4c2a_3.5.8-0ubuntu3.1_i386.deb)
  404 Not Found [IP : 91.189.88.140 80]


W: Échec de la récupération de [http://archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.8-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/kdenetwork/kopete_3.5.8-0ubuntu2_i386.deb)
  404 Not Found [IP : 91.189.88.40 80]

[/COLOR][/SIZE]

---

### Post by Peter09 on 2009-05-11
Are you connected to the internet?

---

### Post by m3asmi on 2009-05-11
Yes I am connecting whith internet

---

### Post by Peter09 on 2009-05-11
what happens with

```
ping [SIZE=2][COLOR=Black]91.189.88.40 80[/COLOR][/SIZE]
```

---

### Post by Partyboi2 on 2009-05-11
> **m3asmi said:**
> Yes I am connecting whith internet
Hi, looks like you could be using an old version of Ubuntu, what version  are you using? If unsure you can open a terminal and check with
```
lsb_release -d
```

---

### Post by m3asmi on 2009-05-15
I use UbuntuME 7.10
I can not install other version because my graphiq carte is with the low quality

---

### Post by Partyboi2 on 2009-05-15
Gutsy has reached its end of life, it is recommend to upgrade to a later release. If you want to continue using Gutsy and install packages, but not receive security updates (not recommended) you can comment out your current gutsy repos from your sources.list and add
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
```

---

### Post by m3asmi on 2009-05-24
I don't understand what is mean  
can u explain it for me

---

