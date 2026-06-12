---
title: "Running Windows Programs on Ubuntu"
date: 2008-10-02
forum: General Help
---

### Post by hg2491 on 2008-10-02
Hey guys,

I would like to install Delphi on a laptop that is running Ubuntu 8.4. The computer has Crossover Linux installed.

Does anyone mind to share how this must be done?

Tanks in advanced,

Johnn.

---

### Post by arkticcool on 2008-10-02
Delphi is made for windows. I don't know if it would work in WINE, however there are (or were) two alternatives to Delphi for Linux. Kylix was created by Borland, but later discontinued so I guess you won't want something that is unsupported.

The second option is Lazarus. It is currently supported and can be run on Linux;
```
sudo apt-get install tct
```

---

### Post by hg2491 on 2008-10-03
Thanks, but Delphi is needed since it is to be use for school.

---

### Post by binbash on 2008-10-03
crossover linux does not officially support Delphi, tho you can try.

Delphi 7 marked as Platinum at wine :

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2325&iTestingId=24372](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2325&iTestingId=24372)

---

### Post by hg2491 on 2008-10-03
So it would be better for me to install Delphi on a virtual machine?

---

### Post by MaxIBoy on 2008-10-03
If it's marked as platinum for WINE, you'll want to use WINE instead of taking the risk with something else. (Crossover is based on WINE, but I'm not sure how well it keeps up with updates to WINE.)

Follow these instructions to get WINE if you don't have it already:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
From there, just right-click on the program and open it with WINE.

---

### Post by binbash on 2008-10-03
Try to install with wine.It marked platinum at version 1.1.4.If it does not work you should run it via virtual machine

---

### Post by Sef on 2008-10-03
> So it would be better for me to install Delphi on a virtual machine?


Yes it would be.

---

### Post by hg2491 on 2008-10-03
I will later need to install Visual Studio and other sorts of Windows programming program, so I will go with the virtual machine.

I have tried to install VMware but failed to do so. I had VirtualBox installed but I find it to be slow and crappy.

How can I install VMware? :frown:

---

