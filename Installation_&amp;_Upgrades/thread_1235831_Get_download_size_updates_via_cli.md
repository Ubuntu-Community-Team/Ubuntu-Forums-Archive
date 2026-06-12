---
title: "Get download size updates via cli"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by VCoolio on 2009-08-09
Is there a command to get the download size (and maybe even installed size) of the total available updates? Update manager shows dl size, so that should also be possible via commandline, shouldn't it? 

If there is not a straightforward command then maybe with python it can be retrieved. In /usr/lib/python2.6/dist-packages/apt/cache.py there are definitions that could be useful (requiredDownload and additionalRequiredSpace, lines 141-152). I have no idea though how to turn that knowledge into a python script that prints dl size for current available updates list (python /usr/lib/update-notifier/apt_check.py --print-packages). 

Help is appreciated.

---

### Post by wojox on 2009-08-09
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-update](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-update)

---

### Post by ajgreeny on 2009-08-09
Try ```
sudo apt-get -s install packagename
```or ```
sudo apt-get -s upgrade
``` which will simulate the action you ask for but not do anything, so you will see the size of download without the download happening.

---

### Post by VCoolio on 2009-08-09
Thanks for replying but the -s flag doesn't show download size. So I need to actually issue the root permission install / upgrade command and answer 'no' to the continue-question (if any) to get the download size? Update manager shows it before I have to enter the password, so I hope someone has an alternative solution.

---

