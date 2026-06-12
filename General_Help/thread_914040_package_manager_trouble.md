---
title: "package manager trouble"
date: 2008-09-08
forum: General Help
---

### Post by Auximenes on 2008-09-08
After returning home after one month in Japan, I found out my Ubuntu 7.10 suddenly was unable to perform any upgrades or installations:

Running update manager, synaptic or apt-get commands in the terminal gives me the error:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


Well, then I tried to run the command 'dpkg --configure -a', which gives me:

> pontifex@augustus:~$ sudo dpkg --configure -a
Setting up language-support-ko (1:7.10+20070605) ...
Generating locales...
  ko_KR.UTF-8... 


After which it freezes. I've let it stand over night, and nothing more happened. I've heard generating locales takes a long time, but not 6+ hours!

Needless to say, an Ubuntu machine with a broken package manager is not worth much, so I would appreciate all the help I can get.

Thanks

---

### Post by tuxxy on 2008-09-08
Try


```
apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by jerome1232 on 2008-09-08
This launchpad bug seemed to have a few relevant answers for your problem (although the bug itself is for upgradeing gutsy-hardy)

[https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340](https://bugs.launchpad.net/ubuntu/+source/langpack-locales/+bug/249340)

this thread had a few solutions which one of them was to try sudo dpkg --configure a again.

[http://ge.ubuntuforums.com/showthread.php?t=865679&page=6](http://ge.ubuntuforums.com/showthread.php?t=865679&page=6)

---

### Post by Auximenes on 2008-09-08
Thnaks for the links!

> chmod 644 /usr/bin/localedef

solved the problem for me.

Muchos gracias!

---

### Post by haley1 on 2008-09-10
Thanks, this helped me as well. Search does work sometimes. :-)

---

