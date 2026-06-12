---
title: "Updates problem, and theme preferences won't work"
date: 2005-11-27
forum: General Help
---

### Post by PatrickMay16 on 2005-11-27
Today, I've noticed two problems.

I reloaded the package list in Synaptic, and it notified me that there were updated packages to install. I tried to install them, but three of them didn't. The problem is that one of the ones to update wouldn't install because it is depending on something else (cdrdao) that's depending on a version of a library that is newer than the one that is available in the repositories. Does anyone know what's causing this? Or is it a temporary problem with the repositories? In case it helps, here is my sources.list file:

> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## RareWares/Debian Multi-Media Repository for Unstable
deb [http://www.rarewares.org/debian/packages/unstable/](http://www.rarewares.org/debian/packages/unstable/) ./

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/



Also, there's another problem. When I try to change the themes by going to System -> preferences -> theme, I get the "opening themes..." on the task bar. But nothing after that happens and after awhile the "opening themes..." on the task bar disappears. I tried it again a few times but it did the same thing. Then I looked in the system monitor and saw that there were several "gnome-theme-manager"s running. Also, after that, the system -> log out option would not do anything any more.
As a temporary fix to the problem, I found that after doing "killall gnome-theme-manager", going to system - preferences - theme would open the theme dialog properly and the logout dialog would work properly again. Though I'd like to fix this problem anyway.
Can anyone help?

---

### Post by PatrickMay16 on 2005-11-27
I found out what was causing the problem with the update cdrdao. One of the repositories I had (the Rarewares one) was causing that problem. Since everything I need from that repository is installed, I've removed its entry from my sources.list file. Also, I changed my sources.list file to ubuntu_demon's recommended breezy sources.list file: [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

And that problem is fixed.

---

### Post by endersshadow on 2005-12-11
I have exactly the same problem with the Themes/Logout dialog.  I've noticed that when this happens, the computer is running two instances of gnome-theme-manager, though I have no idea why.  Whenever I try to start it from CLI, it just hangs and I have to Ctrl+C out of it.  I'll do some more research on why this is happening...

---

### Post by endersshadow on 2005-12-11
It seems connected to dual instances of update notifier running.  Check your system monitor and kill update notifier, and all should be fine.

---

