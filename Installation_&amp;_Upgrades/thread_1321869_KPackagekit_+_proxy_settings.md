---
title: "KPackagekit + proxy settings"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by tomarctus on 2009-11-10
Hi!

I have some strange problems with KPackagekit, and apt-get. The problem is simple, but I don't know what to do with it. >.< I have switched my proxy settings a week ago, the strange thing is that KPackageKit still uses these preferences after I have switched back it to direct connection to internet.... >.>
I know this only because I have switched my proxy preferences to [http://0:3333](http://0:3333), but still direct connection is selected, and as I try to update, he tells me that [http://0:3333](http://0:3333) refused the connection....... -.-"
And 1 more thing: aptitude works still fine.

Any suggestions?

---

### Post by solar george on 2009-11-15
try just deleting the proxy address in the settings and ignoreing the error message that it gives when you press ok

---

### Post by Ajat on 2009-11-17
Did you modified the /etc/apt/apt.conf? 


I also experience the same thing.. i can  update the sources.list via Kpackagekit (clicking reload).. and it download the packages smoothly.. BUT, if i use it to download a selected package.. it's failed to download any package (it say unable  to connect to 152.118.24.10:8080 which is my university proxy address.)
not i'm stick with apt-get method

Restoring the apt.conf (let it blank) does NOT fix this ..


any ideas?

---

### Post by solar george on 2009-11-17
No i was refering to the proxy settings in the kde System Settings > Networking > Proxy under the setup button for Manual if you have changed those.

---

### Post by Ajat on 2009-11-19
do you have gnome installed? i try aptitude from gnome but it uses proxy..

i've checked with echo http_proxy

---

### Post by Ajat on 2009-11-21
I solved it.. since the gnome doing fine.. the problem is inside the kde.. it's actually

```
sudo kate .kde/share/config/kioslaverc 
```

change it to look like below

```

PersistentProxyConnection=false

[$Version]
update_info=kioslave.upd:kde2.2/r1,kioslave.upd:kde2.2/r2,kioslave.upd:kde2.2/r3

[Notification Messages]
WarnOnLeaveSSLMode=false

[Proxy Settings]
AuthMode=0
NoProxyFor=
Proxy Config Script=
ProxyType=0
ReversedException=false
ftpProxy=
httpProxy=
httpsProxy=
```

---

### Post by alamuru420123 on 2009-12-05
@Ajat:

Thanks so much dude, that's been a nuisance for me. Weird that this file doesn't get reset even after changing the kde proxy settings.

---

### Post by vyk on 2010-01-22
:KS

Thanks a mill.
This has been bugging me for a while.

---

### Post by amadeus244 on 2010-02-06
Thanks a lot it works for my. do you know if this is a reported bug ? is this an ubuntu or KDE's bug ?

---

### Post by batcat on 2010-02-13
Thanks [Ajat]("http://ubuntuforums.org/member.php?u=866331") I was having trouble with this too :o)

---

### Post by digithom on 2010-03-09
Thanks a lot Ajat, this works for me too.

---

