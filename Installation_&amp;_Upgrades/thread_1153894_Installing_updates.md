---
title: "Installing updates?"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by anili100 on 2009-05-09
Hi!
I have installed Ubuntu on my desktop couple of weeks ago, and I have just connected it to the internet. It says that I have 360 updates available, but when I try to install them, a message like this comes out: 
> 
An error occured:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I opened terminal, I typed 'dpkg --configure -a' and this is what I got:
```
lj@lj-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
```
Any ideas what to do next?
Thanks in advance!

---

### Post by spcwingo on 2009-05-09
Just put sudo (super user do) in front of that command.  It should look like this:

```
sudo dpkg --configure -a

```

---

### Post by anili100 on 2009-05-09
Thanks :) I've realised I asked a silly question.
Anyway, I've run the command and it won't work again. Here's my output:
```
lj@lj-desktop:~$ sudo dpkg --configure -a
[sudo] password for lj: 
dpkg: dependency problems prevent configuration of qt3-assistant:
 qt3-assistant depends on qt3-doc; however:
  Package qt3-doc is not installed.
dpkg: error processing qt3-assistant (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of qcad-doc:
 qcad-doc depends on qt3-assistant; however:
  Package qt3-assistant is not configured yet.
dpkg: error processing qcad-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

```

---

### Post by spcwingo on 2009-05-09
It looks like there's a problem with qt.  Try reinstalling these:

```
sudo apt-get install --reinstall qcad qcad-doc qt3-assistant qt3-doc
```

---

