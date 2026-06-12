---
title: "Disable suspend  when on AC"
date: 2012-11-03
forum: Hardware
---

### Post by demontager on 2012-11-03
I used to connect to my laptop remotely that's why need to keep it  always on, but XFCE power manager doesn't provide an option to disable  suspend when laptop AC powered,  only offers maximum 5 hours 50 mins

[http://6g6.eu/sih0-desk.jpeg](http://6g6.eu/sih0-desk.jpeg)

My system is Lubuntu 12.10, on laptop Asus U36SD

---

### Post by imachavel on 2012-11-03
that's a good question for Ubuntu developers. Have you tried this command in terminal?

sudo apt-get install ubuntu-tweak.

Now look again if the suspend option is there does hibernate work just as well? 

[http://www.techrepublic.com/blog/itdojo/ubuntu-1204-tweaks-re-enable-hibernate-move-the-window-buttons-more/3326](http://www.techrepublic.com/blog/itdojo/ubuntu-1204-tweaks-re-enable-hibernate-move-the-window-buttons-more/3326)

otherwise I just don't know

---

### Post by demontager on 2012-11-03
Yeah, i know this tool long time ago used it on Ubuntu.
I'm not sure if i'm doing right because ubuntu-tweak is going to suck compiz alongside.
Will Lubuntu  feel good after that  :)?
```

sudo apt-get install ubuntu-tweak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-core compiz-plugins-default gir1.2-gconf-2.0 gir1.2-unique-3.0
  libcompizconfig0 libdecoration0 libprotobuf7 python-compizconfig python-lxml
Suggested packages:
  python-lxml-dbg
The following NEW packages will be installed:
  compiz-core compiz-plugins-default gir1.2-gconf-2.0 gir1.2-unique-3.0
  libcompizconfig0 libdecoration0 libprotobuf7 python-compizconfig python-lxml
  ubuntu-tweak
0 upgraded, 10 newly installed, 0 to remove and 4 not upgraded.
Need to get 3,926 kB of archives.
After this operation, 14.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

As to the hibernate - I'm not using it because it waste my SSD space. 
Hope you know that in order to use hibernate need to allocate swap space same amount as RAM.  My SSD is 128 GB and i have 8 Gb RAM so i don't want to keep 8 GB swap just for hibernate. Anyway U36SD so fast  that almost no deference between hibernate and suspend, SSD makes his job very well.

---

