---
title: "KDM missing after 4.1 to 4.2 upgrade"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by diskace on 2009-02-20
Hi friends, here is a weird one for me. I started upgrade in adept and it asked to reboot after it finished downloading and install. Now i am stuck with a nun-functional system.

KDM won't start
/etc/init.d/kdm start; say kdm is currently not install
apt-get install kdm; say it has broken package
apt-get install kubuntu-desktop; say [http://pastebin.com/f5389c17a](http://pastebin.com/f5389c17a)


i ran: 
apt-get update
apt-get clean

Now i don't know what i should do. Any help would be appreciated. thanks.

---

### Post by taurus on 2009-02-20
So I assume it will boot into a console instead of GUI login screen.  Can you log in with your username and password?  Then, see if KDE starts with

```
startx
```
What does your /etc/apt/sources.list look like anyway?

```
cat /etc/apt/sources.list
```

---

### Post by diskace on 2009-02-20
Startx as a user (not root) will result in:

Xsession: Unable to start X session --- no /home/user/.xsession file no /home/user.Xsession file , no session managers, no windows managers and no terminal found; aborting

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Bug Fix
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## Repositories ENTIRELY UNSUPPORTED (universe + multiverse) 
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates universe

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Backports = new software
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

---

### Post by diskace on 2009-02-20
Just added the code below to the source.list and it seems to proceed now. The update process through adept did not specify that you have to add this repository.

```

deb [http://ppa.launchpad.net/kubuntu-experimental/ubuntu](http://ppa.launchpad.net/kubuntu-experimental/ubuntu) intrepid main
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
apt-get update
apt-get install kubuntu-desktop

```

---

### Post by diskace on 2009-02-20
Fixed

---

