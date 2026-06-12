---
title: "[SOLVED] opensuse 11 livecd open file as root"
date: 2008-08-08
forum: General Help
---

### Post by savsav on 2008-08-08
I am testing the OpenSuse 11 livecd

I want to open a file as root, but cannot.

The file is /etc/wvdial.conf

That file can only be edited as root.

I tried sudo gedit from terminal but it refuses to launch gedit.

sudo nautilus doesn't work either.

What's the answer?

---

### Post by kellemes on 2008-08-08
> **savsav said:**
> I am testing the OpenSuse 11 livecd

I want to open a file as root, but cannot.

The file is /etc/wvdial.conf

That file can only be edited as root.

I tried sudo gedit from terminal but it refuses to launch gedit.

sudo nautilus doesn't work either.

What's the answer?

Login as root from your login manager..
or from terminal..
```
su
```
or install sudo and add yourself to /etc/sudoers.

---

