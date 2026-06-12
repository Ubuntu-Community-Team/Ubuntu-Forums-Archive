---
title: "libqt3-mt or libqt3c102-mt"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by johnhedge on 2006-01-04
Hi,

I'm trying to install Gambas but I get the following message:

gambas-gb-qt: Depends: libqt3c102-mt (>= 3:3.3.3) but it is not installable

Having Googled I find that libqt3c102-mt has been renamed libqt3-mt.

Q. Is there a way to install libqt3c102-mt?

TIA

John

---

### Post by mazelado on 2006-01-04
I've run into this problem before when trying to install programs that are not from the repository. However, Gambas is in the Universe repository. Are you trying to install it from there? If you are, you shouldn't be having this problem.

---

### Post by DoorGunner on 2006-01-04
I had the same with skype install.....

all i did was try 
sudo apt-get install libqt3c102-mt

if i remember correctly it gave me a little statment that said a newer version was already installed. Give it a try and load the program anyway. Skype worked.

---

### Post by johnhedge on 2006-01-04
I think what I've done is install libqt3-mt and then try to install Gambas from the Gambas download depository. I've now uninstalled libqt3-mt which has uninstalled a heap of other libraries and programs that depend on it.

There was a partial Gambas install left on the system which I've now uninstalled as well. I hope I'm now back to a 'start' position.

I then tried:

# apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate

but no luck.

My sources.list is the recommended one from Ubuntu with universe etc. enabled.

John

---

