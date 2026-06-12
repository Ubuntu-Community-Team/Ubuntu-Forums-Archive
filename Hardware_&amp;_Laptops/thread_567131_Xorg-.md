---
title: "Xorg-"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by vincenzoo on 2007-10-04
Hello you all.
I'm new in this forum!
I'm an Ubuntu user and i had a problem with X-server.
Some time ago i deleted it from my pc. When I reinstalled and reconfiguarated it, the result revealed bad.
i have an ATI 9950 256MB. 
i saw some guides and howtos, but i couldn't repair the Xorg.

I hava a question...which drivers does Xorg load?

Hello!

EDIT: ops! i forget to say you that if i enter in safe mode (as a root) and if i hit startx, the desktop work very well.



ps: Sorry for the errors. I'm Italian.

---

### Post by dabl on 2007-10-04
> **vincenzoo said:**
> 

ps: Sorry for the errors. I'm Italian.

Hah! Then you will especially appreciate what this fellow has done to make your life so much easier:

[http://albertomilone.com/](http://albertomilone.com/)

Click "Projects" and then "Envy".  Follow the instructions to download the .deb file, install it on your system, and then run Envy to install the best ATI driver for your card.

:)

---

### Post by vincenzoo on 2007-10-04
mmm... I must admise: i'm noob. lol.
i did this, but i don't understand a thing....

**root@vincenzoo:/media/scambio#** sudo dpkg -i envy_0.9.7-0ubuntu12_all.deb
Selecting previously deselected package envy.
(Reading database ... 161827 files and directories currently installed.)
Unpacking envy (from envy_0.9.7-0ubuntu12_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy
[B]root@vincenzoo:/media/scambio# 
root@vincenzoo:/media/scambio# [/B]sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  envy: Depends: module-assistant but it is not going to be installed
        Depends: dh-make but it is not going to be installed
        Depends: dpatch but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[B]root@vincenzoo:/media/scambio# 
root@vincenzoo:/media/scambio#[/B] sudo apt-get install module-assistant dh-make dpatch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  envy: Depends: xserver-xorg-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
______________________

What can i do?

> The following packages have unmet dependencies:
envy: Depends: xserver-xorg-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
what does it means?
can i try to do "sudo apt-get -f install"         ...install what?

---

### Post by dabl on 2007-10-04
Hmmm -- that's a lot more trouble than Envy gave me last week when I installed it on Gutsy Beta.

Yes, follow the instruction and try a ```
sudo apt-get -f install
``` and see if xserver-xorg-dev is installed.  If not, then try ```
sudo apt-get -f install xserver-xorg-dev
``` and see if it installs.  If yes, then install Envy again and it should cooperate.  :)

---

### Post by vincenzoo on 2007-10-05
i'm so sad.

I tried
```
sudo apt-get -f install
```
then
```
sudo apt-get -f install xserver-xorg-dev
``` 
then i tried again to do:
```
sudo dpkg -i envy_0.9.7-0ubuntu12_all.deb 
```
after the reboot i undersood that it didn't anything!

--i saved what the bash told me when i typed```
 install -f
```:
> sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  beryl-settings-bindings kdeedu-data kgeography-data libberylsettings0
  ttf-sjfonts libemeraldengine0 libberyldecoration0 libntfs-3g0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dh-make dpatch module-assistant xserver-xorg-dev
Recommended packages:
  patchutils
The following NEW packages will be installed:
  dh-make dpatch module-assistant xserver-xorg-dev
0 upgraded, 4 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 502kB of archives.
After unpacking 2744kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/main xserver-xorg-dev 2:1.2.0-3ubuntu8 [296kB]
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/universe module-assistant 0.10.10 [88.5kB]
Get:3 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/main dh-make 0.42 [33.6kB]
Get:4 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) feisty/main dpatch 2.0.21 [84.3kB]
Fetched 502kB in 4s (118kB/s)
Selecting previously deselected package xserver-xorg-dev.
(Reading database ... 162177 files and directories currently installed.)
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.2.0-3ubuntu8_i386.deb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.10_all.deb) ...
Selecting previously deselected package dh-make.
Unpacking dh-make (from .../archives/dh-make_0.42_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.21_all.deb) ...
Setting up xserver-xorg-dev (1.2.0-3ubuntu8) ...
Setting up module-assistant (0.10.10) ...
Setting up dh-make (0.42) ...
Setting up dpatch (2.0.21) ...
Setting up envy (0.9.7-0ubuntu12) ...
root@vincenzoo:~# 


can i resolve my problem?

---

### Post by vincenzoo on 2007-10-05
What a splendid Program this Envy!
I resolved my problem with two clicks!
Entering in safe mode and typing startx, i used this program with the GUI.
So i repaired my Xorg.

ps: this program has selected also  all the correct resolutions!
Thanks for the support man!

---

### Post by dabl on 2007-10-05
Great!  I knew it would work if you had patience to work with it!  Glad to hear "success".  :guitar:

---

