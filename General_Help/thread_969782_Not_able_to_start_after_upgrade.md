---
title: "Not able to start after upgrade"
date: 2008-11-03
forum: General Help
---

### Post by nazgul42 on 2008-11-03
I have just upgraded from ubuntu 8.04 to 8.10.  When I was running 8.04, it worked pretty well.  Now, when I try to log in, it accepts my username and password, goes to an orange screen that I normally see for less than a second, and stays there.  I can Ctrl-Alt-Backspace to go back to the login and I can move the mouse cursor around, but other than  that, there is nothing, not even the login sound that Ubuntu normally plays.  I can login using failsafe mode though.  I am using gnome, but I do have KDE installed.  Thanks in advance.

---

### Post by Pro-reason on 2008-11-03
You probably need to fix your video drivers.

Try this:

```

sudo apt-get install envyng-gtk envyng-core
sudo envyng -t

```

---

### Post by nazgul42 on 2008-11-03
that didn't help... still same problem

---

### Post by mempman on 2008-11-03
try creating a new user account and from the command line.  I.E. hit ctrl+alt+f1-f7.  after you have created this new user account, try loggin in with that.

---

### Post by nazgul42 on 2008-11-03
creating a new user doesn't help either

---

### Post by kostkon on 2008-11-03
Which graphics card do you have? You could check [this article]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html") to see if any of the solutions offered applies to you.

---

### Post by nazgul42 on 2008-11-03
I have a GeForce 6200
If I select failsafe GNOME from the change session menu at the login prompt, everything seems to work fine...

---

### Post by Pro-reason on 2008-11-05
Do a fresh install of Intrepid.  Many people are having problems with upgrades from within Hardy.

---

