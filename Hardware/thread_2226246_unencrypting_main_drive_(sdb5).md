---
title: "unencrypting main drive (sdb5)"
date: 2014-05-26
forum: Hardware
---

### Post by Raphael_Treccani-C on 2014-05-26
hello, i recently swapped to a new SSD on my laptop , and reinstalled ubuntu 14. during installation i accidentally encrypted sdb5, this is really annoying me, as it means i have to be present for my laptop to load up, and i dont have any important files. i cant find anything online pertaining to removing the encryption. I dont have the bandwidth to download and reinstall Ubuntu, but i dont mind losing files. can anyone help me remove the crypt from my drive ? :) 

ps: i'm pretty confident with command lines and editing system files :)

---

### Post by WinEunuchs2Unix on 2014-05-26
You can unencrypt your files.  I did it to mine over the weekend.  I had to copy my /home directory to /home.backup and create a new user ID (I chose Superman *shrugs*) with sudo (read root) privaledges so I could unencrypt my own user ID.  Just google "unencrypt Ubuntu" and you will find this guy: [http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/](http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/) who explains it.  I also looked at another site or 2 in my research (one cannot have too many testimonies).

Give yourself a couple of hours in your budget.

---

