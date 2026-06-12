---
title: "Debian to Ubuntu"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by mrblowtatoes on 2005-12-09
Well, i decided to leave windows and move to linux, i did this, and i got debian, i have it installed and working fine, save my Wine emulator, which won't work on sarge. So someone in #WineHQ suggested i switch to ubuntu, and that i could do it from apt-get very simple, they said it was a simple command i had to run, [somehtign about chnageing apt-get soruces then doing a dist-upgrade], and i would effectivly be  Ubuntu instead of Debian

I am posting here to find out how this would be done, i don't have access to a cd burner, so i can't burn new ubuntu cds, and if at all possable, i want to keep the total OS installation under 2GB [includeing KDE], as my HD is only 8GB big.

And the fact that i am very new to linux, people have suggested Ubuntu, so if anyone can help me, i woudl appreciate it emmensly.

---

### Post by matthew on 2005-12-09
It isn't especially difficult, at least for an experienced person. You may run into a bump or two along the way or it could go totally smoothly. Here's what you would do if you decide you want to try:

First, as root open the file /etc/apt/sources.list and delete all of the current contents. Put the following in its place and save.

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

#Backports
deb http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-backports main restricted universe multiverse
```

Now open a terminal and as root type
```
apt-get update
```
followed by
```
apt-get dist-upgrade
```

It is possible that you could need to do this a couple of times. Also, your xwindows configuration wll be updated in the process requiring some input from you so don't go too far during the process. Otherwise, that's it.

---

