---
title: "Unmet Dependencies trying to install KDE 4.2"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by AboSamoor on 2009-01-31
I added the Kubuntu published repository for KDE 4.2 <http://www.kubuntu.org/news/kde-4.2> to my sources. Then I made an update [http://paste.ubuntu.com/111986/](http://paste.ubuntu.com/111986/). Then I made an upgrade [I had KDE 4.1] and faced an unmet dependency ! [http://paste.ubuntu.com/111987/](http://paste.ubuntu.com/111987/)

I tried the suggest solution using install -f and I got this error [http://paste.ubuntu.com/111988/](http://paste.ubuntu.com/111988/).

Please, help me. If the solution is not clear just figure where I can search or find resources to understand the problem.

Thanks in advance

---

### Post by gjoellee on 2009-01-31
> **AboSamoor said:**
> I added the Kubuntu published repository for KDE 4.2 <http://www.kubuntu.org/news/kde-4.2> to my sources. Then I made an update [http://paste.ubuntu.com/111986/](http://paste.ubuntu.com/111986/). Then I made an upgrade [I had KDE 4.1] and faced an unmet dependency ! [http://paste.ubuntu.com/111987/](http://paste.ubuntu.com/111987/)

I tried the suggest solution using install -f and I got this error [http://paste.ubuntu.com/111988/](http://paste.ubuntu.com/111988/).

Please, help me. If the solution is not clear just figure where I can search or find resources to understand the problem.

Thanks in advance

Try using this command:
```
sudo apt-get upgrade -f
```

or/and install:
```
sudo apt-get install kde.icons-oxygen
```

(you might need to add the "-f" (force) option there as well

---

### Post by Partyboi2 on 2009-01-31
> **AboSamoor said:**
> I added the Kubuntu published repository for KDE 4.2 <http://www.kubuntu.org/news/kde-4.2> to my sources. Then I made an update [http://paste.ubuntu.com/111986/](http://paste.ubuntu.com/111986/). Then I made an upgrade [I had KDE 4.1] and faced an unmet dependency ! [http://paste.ubuntu.com/111987/](http://paste.ubuntu.com/111987/)

I tried the suggest solution using install -f and I got this error [http://paste.ubuntu.com/111988/](http://paste.ubuntu.com/111988/).

Please, help me. If the solution is not clear just figure where I can search or find resources to understand the problem.

Thanks in advance
You could try 
 ```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/kde-icons-oxygen_4%3a4.2.0-0ubuntu1~intrepid1~ppa3_all.deb
```

---

### Post by AboSamoor on 2009-01-31
Thanks Partyboi2 it worked fine with the force overwriting option ;)

---

