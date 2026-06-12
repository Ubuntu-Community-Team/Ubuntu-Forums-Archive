---
title: "Bare Desktop System without apps?"
date: 2009-03-25
forum: Installation &amp; Upgrades
---

### Post by ddastoor on 2009-03-25
Hi, how can I install KDE, XFCE (or any desktop system, in general) on top of Ubuntu 8.10 without the apps that come shipped with that desktop system?

Basically,
1) I installed Ubuntu 8.10.
I therefore have my whole range of gnome apps installed.

2) Then I do a :-
"apt-get install kubuntu-desktop".

Now, I want ONLY the KDE desktop, not the KDE apps that come shipped with this, except if I have an option to install ONLY very selective KDE apps too?

THanks.

---

### Post by kerry_s on 2009-03-25
sudo apt-get install kde-core
sudo apt-get install xfce4

just don't use any of the *-desktop packages those are distro meta packages, aka: list of things to install.

---

### Post by ddastoor on 2009-03-26
> **kerry_s said:**
> sudo apt-get install kde-core
sudo apt-get install xfce4


Thanks a lot, will try that.

---

