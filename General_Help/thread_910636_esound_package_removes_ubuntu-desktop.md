---
title: "esound package removes ubuntu-desktop?"
date: 2008-09-04
forum: General Help
---

### Post by XanTrax on 2008-09-04
So, I was trying to install ET for Linux following this guide:

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)

And of course, I run into the sound problem that is stated in the bottom of that tutorial.  I install esound and do what it says to do and it still doesnt work.  So, I figure a restart is required.  I restart, login, and then nothing seems to load anymore.  Only my background shows.  So, I do a little digging around in logs and see that installing esound removes pulseaudio-esound-compat and ubuntu-desktop.  Figuring ubuntu-desktop IS what it is sounds, I purge esound and reinstall ubuntu-desktop.  Then, everything seems to load fine as normal.  

This shows when you install esound
```

[18:32:17][eax@kozler-linux:~]$ sudo apt-get install esound
[sudo] password for eax: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**The following packages will be REMOVED:**
  **pulseaudio-esound-compat [COLOR="Red"]ubuntu-desktop[/COLOR]**
The following NEW packages will be installed:
  esound
0 upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/27.7kB of archives.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? 

```

So, not entirely knowing what ubuntu-desktop was, I looked in synaptic.

> 
The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.



So, my question is, why does installing esound remove one of the most necessary components for Ubuntu desktop environment to run?


Thank you for your time

---

### Post by XanTrax on 2008-09-05
Bump, I think this is kind of really important?

---

### Post by Nepherte on 2008-09-05
As what I know of, ubuntu-desktop is just a virtual/meta package. If you install it, it will actually install all the programs linked to it. If you remove one of those programs, you don't have all the programs in ubuntu-desktop, so the virtual package gets removed. It won't remove any other package. I don't have ubuntu-desktop either. If things get messed up, you can simply reinstall it with:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by XanTrax on 2008-09-06
> **Nepherte said:**
> As what I know of, ubuntu-desktop is just a virtual/meta package. If you install it, it will actually install all the programs linked to it. If you remove one of those programs, you don't have all the programs in ubuntu-desktop, so the virtual package gets removed. It won't remove any other package. I don't have ubuntu-desktop either. If things get messed up, you can simply reinstall it with:
```
sudo apt-get install ubuntu-desktop
```


Hi,  Thank you for replying.

I knew that reinstalling it would fix it but I know for sure that if you install esound it removes ubuntu-desktop and then when you restart and after login the desktop enviornment wont load.  Thats why I am posting this, to bring this to someones attention.  Maybe its just me and some kind of fluke but I will try in virtual enviornments and see what happens.  I still think this should be looked at, at least a little bit.

---

### Post by XanTrax on 2008-10-15
Sorry for the bump but does anyone know why there are a lot of packages that if you remove them it also removes Ubuntu-Desktop?

---

### Post by xENO_ on 2008-10-15
> So, my question is, why does installing esound remove one of the most necessary components for Ubuntu desktop environment to run?

ubuntu-desktop is a very large meta-package.  If any package is part of the default install in Ubuntu, then it's almost certainly in ubuntu-desktop's dependencies (there are a few exceptions.)

pulseaudio-esound-compat is part of the base Ubuntu install, since many programs use esound, and don't yet support pulseaudio.

According to the pulseaudio webpage, it's possible to run Enemy Territory with pulseaudio.  Read [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by XanTrax on 2008-10-15
> **xENO_ said:**
> ubuntu-desktop is a very large meta-package.  If any package is part of the default install in Ubuntu, then it's almost certainly in ubuntu-desktop's dependencies (there are a few exceptions.)

pulseaudio-esound-compat is part of the base Ubuntu install, since many programs use esound, and don't yet support pulseaudio.

According to the pulseaudio webpage, it's possible to run Enemy Territory with pulseaudio.  Read [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

Thank you for the explanation.  I still find it kind of odd that if you opt to remove a package that it would also take out such a significant part of the Ubuntu environment.  Though its all "packages" I still think that when removing some things it would also remove significant parts of the OS.  Also, I installed esound manually though pulseaudio-esound-compat I believe was already in there.  When I went to remove esound because I still couldnt get sound to work, thats when I was prompted with this.

There was something else I was going to remove that I had installed manually that also wanted to take out ubuntu-desktop.  This time, it was on Intrepid.

All well, thanks again for the explanation.

---

