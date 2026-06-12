---
title: "Upgrade help :("
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by kalias on 2006-01-28
Hi!  I attempted my first upgrade of my ubuntu system to the new version of breezy and it did not go well.  I believe I must have missed a step and now I have no gome or x on my system.  I get some failures during bootup.  I tired the sudo debraphan thing and it also failed.  Anychance someone could give me some help?  Is there anyway to go backwards?

thanks :)

kalias

---

### Post by BenTyreman on 2006-01-28
Perhaps you could outline what steps you performed to upgrade the system.

The general procedure is to ensure ubuntu-desktop is installed by running
```
sudo apt-get install ubuntu-desktop
```

Then, change your sources.list over to breezy. Update apt with
```
sudo apt-get update
```

Then, perform the upgrade with
```
sudo apt-get dist-upgrade
```

After it has run through, you may have to run
```
sudo apt-get -f install
```
to get the last few packages to install.

Once you think everything is installed properly, run
```
sudo apt-get dist-upgrade
```
again, and make sure it says 0 packages were held back and 0 need to be upgraded.

---

### Post by kalias on 2006-01-28
Hi ! Yes, sorry :(  The first thing that I tried was the upgrade from synaptic.  I just did the upgrade as documented.  However, I did not resolve any packages or anything.  When that did not work, I switched to terminal and made the upgrades to a file and started the upgrade using sudo.  This appeared to work but it gave alot of errors mainly perl ones saying the the locale would remain the same.  I am working from memory here so please bear with me.  After the installed sort of completed, there was some things that failed.  Unfortunately, at this point, I accidently powered my machine down.  When I brought it back up again, it sort of works.  I get the ubuntu login but only in text.  Also, there are some failures in the booting process.

hope this helps :)

kalias

---

### Post by BenTyreman on 2006-01-28
It sounds like most of the update worked OK. Try logging in using your standard username and password.

Then, run
```
sudo apt-get -f install
```

This should sort out those last few packages. After you have done that, see what the situation is like by rebooting.

Also, ensure ubuntu-desktop is still installed. If you have removed any packages that in turn removed ubuntu-desktop, some new breezy packages will be missing.

---

### Post by kalias on 2006-01-28
Hi!  I tried that and I get some errors.  They are as follows:

Errors were encountered while processing:
posfix
mailx
mutt
lsb-core

The errors indicate dependency problems.

---

### Post by towsonu2003 on 2006-01-28
what does ```
sudo apt-get check
``` say? you could also try to reconfigure X: backup /etc/X11/xorg.conf and ```
sudo dpkg-reconfigure xserver-xorg
``` if I remember correctly. 

As far as I know, there is no way back.

---

### Post by kalias on 2006-01-29
When I did the sudo apt-get -f install. Those were the errors that I got.

---

### Post by kalias on 2006-01-29
I ran sudo dpkg-reconfigure xserver-xorg and things are now a little better.  I don't get the failures on startup.  I think the install - f fixed this.  The next problem is to get gnome and x up and running.  Neither come up at this point.

---

### Post by kalias on 2006-01-29
So is there anyone out there that could help me bring the rest of my system up?  As per the thread I botched my upgrade.  The current status is that the machine comes up with no errors but only in single user mode without windows.  Where do I need to go and check to get x up and then gnome?  I know some about the linux boot but not all.  Do I need to modify the grub stuff to start with?

I am keen to learn about how linux works so, even though this is a pain, I may learn something useful.

as always thanks for your help :)

kalias

---

### Post by BenTyreman on 2006-01-30
When you get to a command line, does it immediately log you in as root, or do you log in with your username and password?

If you are logged in as root, then you are in single user mode, which means something is seriously misconfigured. If not, then it looks like X is somehow broken.

At the command line, try typing ```
startx
``` and see what happens. If that works, press ```
ctrl+alt+backspace
``` to kill X, then type ```
sudo /etc/init.d/gdm restart
``` and see what happens then.

---

### Post by kalias on 2006-01-31
Yes, you were correct, it was a problem with x.  I am not sure exactly what. I uninstalled and reinstalled it and now it is working.  It did give me a couple of discrepency errors though.  These were with mutt, mailx, postfix, lib-core.  How do I clean those up?

thanks for your help :)

kalias

---

### Post by BenTyreman on 2006-01-31
It should be safe to just remove those packages. I don't have any of those packages installed on a default Dapper installation, which I assume is similar to a default Breezy install.

---

