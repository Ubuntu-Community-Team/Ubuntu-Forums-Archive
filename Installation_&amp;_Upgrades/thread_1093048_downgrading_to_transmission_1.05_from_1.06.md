---
title: "downgrading to transmission 1.05 from 1.06"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by imparja2 on 2009-03-11
transmission version 1.06 constantly stalls and I'm told that people solve this problem by installing the older 1.05 version. Since I'm a beginner I have no idea what type of file I should be looking to install or what application I should use to run the setup please advise

---

### Post by mikewhatever on 2009-03-11
I don't know about 1.05, but perhaps one of the newer versions might work.
[http://www.getdeb.net/search.php?keywords=transmission](http://www.getdeb.net/search.php?keywords=transmission)

---

### Post by Partyboi2 on 2009-03-11
If you are wanting 1.05 you should be able to download [[COLOR=Blue]transmission 1.05[/COLOR]]("https://launchpad.net/ubuntu/hardy/i386/transmission/1.05-0ubuntu1") deb and [[COLOR=Blue]transmission-common 1.05[/COLOR]]("https://launchpad.net/ubuntu/hardy/i386/transmission-common/1.05-0ubuntu1") deb
Then open a terminal and change to where the downloaded deb packages are eg if on Desktop
```
cd ~/Desktop
```then install with
```
sudo dpkg -i transmission-common_1.05-0ubuntu1_all.deb
```then install transmission
```
sudo dpkg -i transmission_1.05-0ubuntu1_all.deb
```

---

