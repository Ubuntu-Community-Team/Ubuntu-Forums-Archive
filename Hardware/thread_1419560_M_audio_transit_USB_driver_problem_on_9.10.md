---
title: "M audio transit USB driver problem on 9.10"
date: 2010-03-02
forum: Hardware
---

### Post by yau_tak on 2010-03-02
I found this thread [https://help.ubuntu.com/community/MaudioTransitUSB](https://help.ubuntu.com/community/MaudioTransitUSB)
pointing me to  [https://launchpad.net/~neil-aldur/+archive/ppa]("https://launchpad.net/%7Eneil-aldur/+archive/ppa")
for a driver, but I couldn't find madfuload after added that site            **ppa:neil-aldur/ppa **as a software source. 
So where can I download this driver which works for 9.10?
Thanks for helping me.

---

### Post by Benny Bauer on 2010-03-12
sudo add-apt-repository ppa:neil-aldur/ppa
sudo apt-get update
sudo apt-get install madfuload 


worked fine for me,

Benny

---

### Post by yau_tak on 2010-03-16
Thanks very much and it has been working well now.

---

