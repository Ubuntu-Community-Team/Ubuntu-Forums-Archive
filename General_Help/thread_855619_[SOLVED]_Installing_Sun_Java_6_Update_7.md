---
title: "[SOLVED] Installing Sun Java 6 Update 7"
date: 2008-07-10
forum: General Help
---

### Post by SammerHammer on 2008-07-10
HI all, I recently visited the Java website and they said that the version of Java on my computer (Sun Java 6 Update 6) is outdated. However, in Synaptic, that is still the latest version. On the Java site, there are links to download the new version. The download file is a *-rpm.bin file. I want to know how to install that correctly on my Hardy computer without any problems. I need this new update of Java to run RuneScape fullscreen correctly, so please, this is urgent. :cry:

---

### Post by pluckypigeon on 2008-07-10
You need to install Alien (An RPM Installer)

```
sudo apt-get install alien
```

Open a Terminal (I'm assuming the file is on your Desktop)

```
cd ~/Desktop
```

Then Convert the RPM to a Deb

```
sudo alien -k JAVA-UPDATE-NAME-GOES-HERE.rpm
```

Then Install the Deb

```
sudo dpkg -i JAVA-UPDATE-NAME-GOES-HERE.deb
```

:popcorn:

---

### Post by Vadi on 2008-07-10
Hm. Unfortunately it looks like update 7 version is only available in the next alpha version of Ubuntu - though it might be available on 8.04 soon.

Edit: Try the above solution, and let us know if you'll need help on any of the commands.

---

### Post by txcrackers on 2008-07-11
I actually wouldn't worry about upgrading, to be honest. When a version of Java starts getting to this release number, they're correcting bugs that a "normal" user wouldn't run into.

However, if you do decide to install the RPM via alien, I'd strongly recommend removing **all** the Java installations that you already have there. And once you do get it installed, you'll probably still have to do some more work to get it working properly: RH and Debian systems handle "non-native" applications a bit differently.

---

### Post by tinny on 2008-07-11
Seriously, don't worry about it!

This is the same version of Java I use and its just fine. (I program in Java for a living ;) )

---

### Post by yct on 2008-07-17
> **tinny said:**
> Seriously, don't worry about it!

This is the same version of Java I use and its just fine. (I program in Java for a living ;) )

True, it's much better to get the one from repositories, for the benefit of having it correctly integrated to the system.

But Eclipse 3.4 (vs. 3.2 from repos) is a different story! :)

---

### Post by tinny on 2008-07-18
> **yct said:**
> But Eclipse 3.4 (vs. 3.2 from repos) is a different story! :)

:confused:

Works fine for me.

---

### Post by pluckypigeon on 2008-07-20
Did you install it? 

Have you messed up your pc?.. seeing as you havent replied yet):P

---

### Post by dynamethod on 2008-07-20
Oh wow, i was just about to start this thread too, my current java installation is:


```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

```

But it is FOREVER crashing in firefox 3, and when i run:

```
pgrep -l java_vm
```

the proccess is still running in the background... and also using %100 cpu

this is driving me crazy, using 32bit Ubuntu 8.04

it dumps an error log in my home folder

```
head *.log

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb3212a3f, pid=6392, tid=3021454224
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b22 mixed mode, sharing linux-x86)
# Problematic frame:
# C  0xb3212a3f


```

Help much appreciated as any and every java applet seems to crash very randomly and very often...

---

### Post by tinny on 2008-07-20
> **dynamethod said:**
> Oh wow, i was just about to start this thread too, my current java installation is:


```
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)

```

But it is FOREVER crashing in firefox 3, and when i run:

```
pgrep -l java_vm
```

the proccess is still running in the background... and also using %100 cpu

this is driving me crazy, using 32bit Ubuntu 8.04

it dumps an error log in my home folder

```
head *.log

#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb3212a3f, pid=6392, tid=3021454224
#
# Java VM: Java HotSpot(TM) Client VM (10.0-b22 mixed mode, sharing linux-x86)
# Problematic frame:
# C  0xb3212a3f


```

Help much appreciated as any and every java applet seems to crash very randomly and very often...

Hey fellow Kiwi ;)

What version of Ubuntu are you running?

Have a look at this site.

[http://www.w3.org/People/mimasa/test/object/java/clock](http://www.w3.org/People/mimasa/test/object/java/clock)

You should see a few clocks. Also while viewing this site open up the Java console. (Java console is available under your "Applications" menu) This may show you some stack traces.

Also try making sure you have all Java 6 related packages (This is what I have and mine works mint under Ubuntu Hardy)

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install sun-java6*

```

---

### Post by dynamethod on 2008-07-20
Thanks for your reply, i have ubuntu 8.04 installed and all the necessary sun-java6 packages installed, not at my machine right now but ill paste the output of dpkg -l '*sun-java*' | grep ^ii once i get back home

---

### Post by ihavenoname on 2008-08-14
well you could technically enable the intrepid repos and install only java.

---

### Post by SammerHammer on 2008-08-23
Thanks to every body for helping me; sorry I wasn't able to post before. Since I have quit RuneScape, I don't have an urgent need for the new Java version, but I might use plucky's method if I get the change.

Also, how do I add Intrepid repos to get the new java in hardy?

---

### Post by lvlo on 2008-08-23
> **SammerHammer said:**
> Thanks to every body for helping me; sorry I wasn't able to post before. Since I have quit RuneScape, I don't have an urgent need for the new Java version, but I might use plucky's method if I get the change.

Also, how do I add Intrepid repos to get the new java in hardy?

Sun Java 6.07 available in Hardy proposed repos:

[[img]http://smages.com/t/9a/72/9a722420b00dba741c101843c1e4f211.jpg[/img]](http://smages.com/9a/72/9a722420b00dba741c101843c1e4f211.png.htm)

---

### Post by SammerHammer on 2008-08-26
lvlo, how do I get those repos?

---

### Post by lvlo on 2008-08-26
> **SammerHammer said:**
> lvlo, how do I get those repos?

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories than "Updates" tab. 

Enable "Unsupported updates (hardy-backports)" than close settings and update packages information ("Reload" button).

You will see many updates, **but be very careful** - install only packages you need very much ( I broke my system few times installed all backports updates :) ) than **disable** Backports repos.

PS: I've installed Sun-Java 6 Update 7 and have no problems with it.

---

### Post by SammerHammer on 2008-08-27
> **lvlo said:**
> System -> Administration -> Synaptic Package Manager -> Settings -> Repositories than "Updates" tab. 

Enable "Unsupported updates (hardy-backports)" than close settings and update packages information ("Reload" button).

You will see many updates, **but be very careful** - install only packages you need very much ( I broke my system few times installed all backports updates :) ) than **disable** Backports repos.

PS: I've installed Sun-Java 6 Update 7 and have no problems with it.

Well, thanks for that. :)
I still have one problem though; because I enabled the pre-released repos, I now have an Update Manager that is trying to force me to update to the new versions, even though I disabled the repo after installing java. Any ideas how to fix this?

---

### Post by lvlo on 2008-08-27
> **SammerHammer said:**
> Well, thanks for that. :)
I still have one problem though; because I enabled the pre-released repos, I now have an Update Manager that is trying to force me to update to the new versions, even though I disabled the repo after installing java. Any ideas how to fix this?

After you've disabled backports (or pre-released) repos, you just need to reload package information ("Reload" button). You need do this every time when you change, add or remove repos.

---

### Post by SammerHammer on 2008-08-27
> **lvlo said:**
> After you've disabled backports (or pre-released) repos, you just need to reload package information ("Reload" button). You need do this every time when you change, add or remove repos.
I've done that so many times, but my update manager is still telling me to upgrade to the pre-release versions.

---

### Post by lvlo on 2008-08-27
> **SammerHammer said:**
> I've done that so many times, but my update manager is still telling me to upgrade to the pre-release versions.

Run this in terminal:

```
cat /etc/apt/sources.list
```

and post the output.

---

### Post by tinny on 2008-08-27
You are wasting your time. ](*,)

Just use Sun Java 6 u6 from the standard repositories. You wont even notice the difference.

---

### Post by SammerHammer on 2008-08-27
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted                                                                        
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to       
# newer versions of the distribution.                                           

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-updates main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy universe                   
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy universe               
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-updates universe           
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-updates universe       

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy multiverse                  
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy multiverse              
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-updates multiverse          
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-updates multiverse      

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-security main restricted
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-security main restricted
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-security universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-security universe
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-security multiverse
deb [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-backports restricted main multiverse universe
deb-src [http://ubuntu.mirror.rafal.ca/ubuntu/](http://ubuntu.mirror.rafal.ca/ubuntu/) hardy-security multiverse
deb [http://zekr.org/apt](http://zekr.org/apt) gutsy main
  ## Medibuntu - Ubuntu 8.04 "hardy"
  ## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

---

### Post by lvlo on 2008-08-27
Run this in terminal (change "gedit" to "kate" if you use KDE):

```
sudo gedit /etc/apt/sources.list
```

comment (insert "#" in the beginning of line) or delete this line:
```
deb http://ubuntu.mirror.rafal.ca/ubuntu/ hardy-backports restricted main multiverse universe
```

and update package information... again :)

---

### Post by SammerHammer on 2008-08-28
> **lvlo said:**
> Run this in terminal (change "gedit" to "kate" if you use KDE):

```
sudo gedit /etc/apt/sources.list
```

comment (insert "#" in the beginning of line) or delete this line:
```
deb http://ubuntu.mirror.rafal.ca/ubuntu/ hardy-backports restricted main multiverse universe
```

and update package information... again :)
Thanks so much. :)
I wonder though, why didn't it work through the GUI? Why did I have to resort to manually editing it?
Anyways, I'll mark this thread Solved.

---

### Post by rjp-lapama on 2008-09-22
Hi Ivlo,
You're a star. Your proposal to enable the proposed updates in the software sources solved the problems I had with Java 6 update 6, as I could not access my bank's webpages anymore in, the otp Applet was dying on me in Firefox. With Java 6 update 7  that apparently has been solved. When the problems first occured with Ubuntu 8.04. I decided to go back to Java 5.  Then my bank pages work again in Firefox, but other application, such as frostwire, didn't work anymore. I have to try them again now!
Cheers, Renee

---

