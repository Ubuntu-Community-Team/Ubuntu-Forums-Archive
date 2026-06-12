---
title: "Need help with Nvidia MSI GTX 970 driver installation"
date: 2015-05-17
forum: Hardware
---

### Post by godzillathecing92 on 2015-05-17
Hi.

I installed this distro a couple of days ago, and I'm trying to get the most out of my GPU on it, both for some games and because I'm stuck on a really low resolution without the drivers.

Problem is, I have no idea how to install drivers on Linux, and I was hoping one of you guys can walk me through this :)

Thanks in advance.

---

### Post by dino99 on 2015-05-17
open a terminal , and run:

> sudo apt-get purge nvidia*
sudo apt-get install nvidia-346

that driver is found on the 'vivid' aka 15.04 version which was released a few days ago.

---

### Post by godzillathecing92 on 2015-05-17
> **dino99 said:**
> open a terminal , and run:



that driver is found on the 'vivid' aka 15.04 version which was released a few days ago.

Thanks for the reply.

Running ```
 sudo apt-get install nvidia-346 
``` gives me this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-346

```

I should probably mention this distro is based on Ubuntu 14.04, and not 15.04..

---

### Post by Bashing-om on 2015-05-17
godzillathecing92; Hello;

Yeah, the package manager is telling you the truth . Version 346 is not available in 14.04's software repository. We have to resort to alternate means to obtain that driver in 14.04. The next step up from the repository to obtain software is from a PPA (Personal Package Archive). In this situation I highly recommend the 'xorg-edgers' PPA.

To do this we work from terminal as the easiest/quickest means to do this. At the login screen key combo ctl+alt+F1 will yield a console interface. Log in here with user name and password ( there will be no response to the screen when password is entered, enter your password blindly and hit the enter key).
At this interface execute the following.
```

sudo service lightdm stop
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346

```
which will :
add the 'xorg-edgers' PPA as a source;
re-sync your system data base;
install the 346 driver.

Reboot the system for the change to take effect:
```

sudo shutdown -r now

```

I expect when you come back up from the reboot ->

[INDENT][INDENT][INDENT]all is rosy in your world
[/INDENT][/INDENT][/INDENT]

---

### Post by godzillathecing92 on 2015-05-17
> **Bashing-om said:**
> godzillathecing92; Hello;

Yeah, the package manager is telling you the truth . Version 346 is not available in 14.04's software repository. We have to resort to alternate means to obtain that driver in 14.04. The next step up from the repository to obtain software is from a PPA (Personal Package Archive). In this situation I highly recommend the 'xorg-edgers' PPA.

To do this we work from terminal as the easiest/quickest means to do this. At the login screen key combo ctl+alt+F1 will yield a console interface. Log in here with user name and password ( there will be no response to the screen when password is entered, enter your password blindly and hit the enter key).
At this interface execute the following.
```

sudo service lightdm stop
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346

```
which will :
add the 'xorg-edgers' PPA as a source;
re-sync your system data base;
install the 346 driver.

Reboot the system for the change to take effect:
```

sudo shutdown -r now

```

I expect when you come back up from the reboot ->[INDENT][INDENT][INDENT]all is rosy in your world
[/INDENT]
[/INDENT]
[/INDENT]


Hello Bashing-om. Thanks for the reply!

I tried doing what you suggested, but unfortunately when I run ```
 sudo service lightdm stop 
```, the screen blinks for a second and then goes completely blank.. After that, only restarting seems to fix it :( Any suggestions?

---

### Post by Vladlenin5000 on 2015-05-17
Just a couple of notes:
1. Stopping lightdm shouldn't be necessary. It is necessary to run the nvidia installer but not for installing drivers from the repositories (Ubuntu official or third-party). I've installed nvidia drivers in hundreds of machines, either the official repository version or from some PPA, and never stopped *lightdm* prior to those installations.
2. It's strongly advisable to ***upgrade*** and ***dist-upgrade*** after *update* and before the actuall nvidia 346 installation. If you had some previous installed it would be automatically upgraded.

---

### Post by godzillathecing92 on 2015-05-17
Yep, just did the same thing minus the lightdm part and my world is as rosy as promised! Thanks guys!

---

### Post by Bashing-om on 2015-05-17
godzillathecing92; Outstanding.

You do good work;
As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

@Vladlenin5000 :)
Sometimes cheap insurance is not a good thing.


[INDENT]there is always that process
[INDENT][INDENT][INDENT]of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

