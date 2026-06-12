---
title: "Frash install keep crashes down"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by motorna_testera on 2009-09-05
first time during the update in "update manager"
than when i tried to install flash plugin for firefox
than when i try to install anything...

first there is an error in installation:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

console always stuck and computer crash at:

Setting up mono-gac (2.0.1-ubuntu0.1) ...
* Installing 1 assembly from libflickrnet2.1.5-cil into Mono
* Installing 1 assembly from libgnome-keyring1.0-cil into Mono
* Installing 7 assembly from libmono-addins0.2-cil into Mono


any help?

---

### Post by stlsaint on 2009-09-05
run that cmd error its giving you in terminal:

sudo dpkg --configure -a

---

### Post by motorna_testera on 2009-09-05
when i run that the thing that i've pasted from console happens...
and freeze...

---

### Post by stlsaint on 2009-09-05
what cmd are you using to install flash plugin

---

### Post by theozzlives on 2009-09-05
you can get flash by just installing ubuntu-restricted-extras from add/remove.

---

### Post by motorna_testera on 2009-09-05
it is not just flash,
its with every install...

i just tried to open Add/Remove
and the same error came out

---

### Post by sray on 2009-09-10
I am facing the same problem, and still looking for solutions.  
I am using Ubuntu Studio 9.04.  After the installation, the system suggested some important security updates including libmono something.  But the update has never succeeded, it always crashes at 

"libmono-addins0.2-cil into mono".

Even I try "sudo dkpg --configure -a" in a terminal, the result is the same: crash!
Any help?  Please!

---

### Post by ztomic on 2009-09-11
same problem here on ubuntustudio 9.04. fresh install then update freezes on mono-gac. have tried 'dpkg -configure -a' several times. am finding plenty of bug reports on mono-gac but no solutions.

---

### Post by orbtlcptn on 2009-09-12
I second(fifth?) the problem, fresh install, did an update, crash, had to restart by force, now can't get apt-get/synaptic to work. Same message about dpkg --configure... , does this, system crashes.
//paco

---

### Post by orbtlcptn on 2009-09-13
Could it be, something wring with the "sources.list" file since it crashes on getting the assembly; here's mine, I don't have a refference to check with but maby someone else got; ```
# 
# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe

#deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://se.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://se.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://se.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

```

---

### Post by BBuntu on 2009-09-15
Same here.

UbuntuStudio 9.04.

HW is new ASRock with Atom 330 and Nvidia ion.

Sometimes system hangs on boot and I can't now install Flash either.

My installation looked OK and problems only started with system update...

---

### Post by jsegel on 2009-09-16
stuck also, apt-get -anything is saying dpkg interrupted, running dpkg --configure -a  freezes the system
awesome.

---

### Post by mvftd on 2009-09-29
Same problem here, Ubuntu Studio 9.04

Strangely, the result of dpkg --configure -a is slightly random. 

It crashes when processing mono-gac, but the number of lines that it outputs (the number of assemblies it compiles, I presume) before crashing varies.

Also, if I cold reboot the system after the crash and retry with dpkg --configure -a, it runs through without attempting to process mono-gac again. 

apt-get dist-upgrade tells me that the package is not fully installed, though. 

I would happily run any diagnosis tool available, if somebody could point it out to me.

 Otherwise Ubuntu Studio runs fine.

---

### Post by Neofita on 2009-09-30
I ain't got a proper solution, but there's a way not to have the "freeze" problem. 

Completely reinstall your version of Ubuntu.
Then in "update manager" DESELECT anything containing the word "mono" (I mean every "lib**mono***", "lib**mono**-*" and "**mono-***"), carefully AVOIDING to install these upgrades. 

Install EVERY OTHER upgrade suggested by "update manager".

This way, there won't be any annoying crash or subsequent error message: 
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." !!! :P :P :P
[B]
IMPORTANT[/B]!!!  
If you want to keep your Ubuntu free from these crashes and following error messages, you'd better NEVER install any programme or library or upgrade somehow related to _Mono_, _Novell_ and so on (to learn more about the Mono controversy, read for instance [http://www.linuxplanet.org/blogs/?cat=1088](http://www.linuxplanet.org/blogs/?cat=1088)). 

The most popular softwares seeming to create trouble are: "openoffice", "openoffice.org", "banshee", "tomboy", "evolution", "mono". 
I tried installing "openoffice.org" and all I got was a crash, and, once again, the same error message we all had before... :(

Another software of this kind is "F-spot", given by default to you at least with the installation DVD of Ubuntu Studio 9.04.  KEEP IT as it is and DON'T upgrade it!
I even tried to uninstall it, and, guess what, I had a crash and the infamous error message!  :confused:


There's a list of many of these Mono software releases: [http://www.mono-project.com/Software](http://www.mono-project.com/Software)   
There's also a list of many of these Mono libraries: [http://www.mono-project.com/Libraries](http://www.mono-project.com/Libraries)

I'm not an enemy nor a friend of Mono, Novell and so on... 
I just want my Ubuntu Studio 9.04 to keep working without any problem!
I hope this post could be of any help... ;)

---

