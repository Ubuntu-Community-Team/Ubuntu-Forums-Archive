---
title: "Restarting an update and/or upgrade"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by darwinj on 2009-07-12
Where I live my ISP is not very reliable. Sometimes it works good and sometimes it does not work at all. This is no problem when browsing the internet, however it is a problem when downloading something. My concern is when I am updating or upgrading. How do I restart the proccess after it is stopped. For instance, I was upgrading Ubuntu desktop 8.04 to 8.10 when I lost not only the internet connection, but power also. Once everything came back on I just clicked the upgrade button and everything looked normal. On restart it would not boot at all. Not even in the safe mode. The memory test would not work either. I reinstalled 8.04 (I have a dual boot system and had to figure out how to reinstall) and would still like to upgrade. I started the upgrade proccess again and the ISP fail about halfway through. What is the best way to restart the proccess. I can use the command line or the GUI, it does not matter to me which I use as long as it works.
Thank you,
Darwin

---

### Post by Partyboi2 on 2009-07-13
Hi, you should be able to use these commands
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get upgrade
```

---

### Post by darwinj on 2009-07-16
Thank you. I knew that is should be something simple. I will give it a try soon.

---

