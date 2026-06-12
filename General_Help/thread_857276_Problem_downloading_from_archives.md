---
title: "Problem downloading from archives"
date: 2008-07-12
forum: General Help
---

### Post by jobo1313 on 2008-07-12
I dont know if any one else has this problem but when ever i upgrade my ubuntu 8.04 installation i cant fetch anything from the archives. I go to the package manager to download something for my laptop and i get an error saying it cant fetch the archive and the connection is fused. But i still can surf the web ridiculously fast. 
Please Help

---

### Post by PmDematagoda on 2008-07-12
Are you behind a proxy by any chance?

---

### Post by SkonesMickLoud on 2008-07-12
Try:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by jobo1313 on 2008-07-12
I was but i turned it off and it does no good. Could it be my dads desktop. It has XP and he installed this Printmaster and he has been having problems. He thinks that it is the new adobe uprgade, but i have no idea.

---

### Post by jobo1313 on 2008-07-12
Safe upgrade doesnt work tried it from terminal I CANT FETCH.

---

### Post by boblemur on 2008-07-12
can you:

```
ping au.archive.ubuntu.com
ping 91.189.88.46

```

so you can rule out connectivity probs...

---

### Post by jobo1313 on 2008-07-12
PING au.archive.ubuntu.com (91.189.88.45) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=1 ttl=47 time=86.2 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=2 ttl=47 time=85.9 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=3 ttl=47 time=104 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=4 ttl=47 time=86.4 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=5 ttl=47 time=86.6 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=6 ttl=47 time=87.9 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=7 ttl=47 time=100 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=8 ttl=47 time=87.9 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=9 ttl=47 time=963 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=10 ttl=47 time=86.9 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=11 ttl=47 time=94.9 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=12 ttl=47 time=88.2 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=13 ttl=47 time=85.5 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=14 ttl=47 time=88.3 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=15 ttl=47 time=89.6 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=16 ttl=47 time=86.8 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=17 ttl=47 time=90.5 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=18 ttl=47 time=85.6 ms
64 bytes from prat.canonical.com (91.189.88.45): icmp_seq=19 ttl=47 time=86.4 ms

--- au.archive.ubuntu.com ping statistics ---
26 packets transmitted, 26 received, 0% packet loss, time 24991ms
rtt min/avg/max/mdev = 85.592/123.458/963.142/168.023 ms

---

### Post by boblemur on 2008-07-12
hmmm ok so you can connect to the server, its just some strange settings somewhere... make sure ur repos are enabled correctly... ummmm also try in synaptic and see if its the same ( lol soz just guessing here really)

---

### Post by jobo1313 on 2008-07-12
Dude it worked last night, right before upgrade. Still this is way better then Windows' upgrades which literally killed my computer and games and folders and homework. I am glad this is the only that happens to ubuntu.

---

### Post by drs305 on 2008-07-12
Maybe we should step back. Have you looked at your sources.list to see if anything changed after the upgrade? If anything is questionable, or you simply don't know, post:
```
 cat /etc/apt/sources.list | grep -v "^#"
```

---

### Post by nikgare on 2008-07-12
You can go to:

**System->Adminstration->Software Sources**

Select:

**Download From->Other**

And then click:

**Select Best Server**

---

### Post by avtolle on 2008-07-12
A thought; go to Synaptic (System>>Administration>>Synaptic Package Manager) and then click on Settings, click on Preferences, and I believe it is on the top page, see whether the direct connection to the internet radio button is selected. You mentioned that you had "turned off" the proxy, but this change may not have bee picked up by Synaptic.

---

### Post by jobo1313 on 2008-07-12
I dont know:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse



deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by SkonesMickLoud on 2008-07-12
Just a general FYI, anytime you make any changes to your sources you should run "sudo aptitude update" and/or click "Reload" in Synaptic.

Sometimes changes aren't recognized by apt-get/aptitude/synaptic until you reload your source.lst.

---

### Post by jobo1313 on 2008-07-12
No new server was found by the computer.

---

### Post by jobo1313 on 2008-07-12
I reloaded them already.

---

