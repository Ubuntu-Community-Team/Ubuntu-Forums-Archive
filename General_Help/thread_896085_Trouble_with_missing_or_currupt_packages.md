---
title: "Trouble with missing or currupt packages"
date: 2008-08-20
forum: General Help
---

### Post by colobix on 2008-08-20
Hi all.
It started when I tried to update some plugins. I found out that nothing really worked when I tried to update.
Someone here told me that it was maybe the server so I changed it some times to see if it worked, but no luck.
When I found out that it had to be a problem on my PC I tried some different recovering modes to see if I could fix the packages.
It couldn't fix them but it found some, so it told me t try sudo apt-get update or sudo --fix-missing.
Nothing have worked so far so I don't really know what to do now.

I really need help here, so please.

Thank you.

---

### Post by cdtech on 2008-08-20
Try this on a command line:
"sudo dpkg --configure -a && sudo apt-get -f install"

Then try the update.

---

### Post by colobix on 2008-08-20
Thanks but no luck.
I got the same message when i opened the update manager:
"Not all updates can be installed"
And on terminal:
"0 to install, 25 not upgrated, 0 to remove"
But thanks anyway.
Any other solutions?

---

### Post by colobix on 2008-08-20
When I click on the button that makes me able to install some of the updates I get this message:

Can't guess meta-package

Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.

Please Help !

---

### Post by Cheesehead on 2008-08-20
If you've borked your system with a dependency or version conflict (which is why it can't upgrade - the wrong package conflicting packages or wrong version or multiple versions installed somewhere), then you have two ways out.

The clever way - you can figure out which package(s) are causing the problem and resolve the conflict, thereby breaking the logjam. This may be time-consuming. Start by comparing the output between the following two commands to get clues:
```
sudo apt-get -sv dist-upgrade
sudo apt-get -sv dselect-upgrade
```

The brute force way - install one of the meta-packages and upgrade.
```
sudo apt-get install ubuntu-desktop && sudo apt-get dist-upgrade 
```
Since your system is probably customized (you removed a meta-package, for example) this approach might undo some of your customization, and might break any specialty packages or .debs that were relying on specific dependencies that you just upgraded from.

---

### Post by colobix on 2008-08-20
OK thank you. Here is the output from terminal on the first method u mantioned: What does it tell you? I'm green here.

chris@chris-laptop:~$ sudo apt-get -sv dist-upgrade
apt 0.7.9ubuntu17 for i386 compiled on Apr 22 2008 15:19:47
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
chris@chris-laptop:~$ sudo apt-get -sv dselect-upgrade
apt 0.7.9ubuntu17 for i386 compiled on Apr 22 2008 15:19:47
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
chris@chris-laptop:~$

---

