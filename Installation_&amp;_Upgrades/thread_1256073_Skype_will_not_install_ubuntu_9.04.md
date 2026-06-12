---
title: "Skype will not install ubuntu 9.04"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2009-09-02
Trying to install skype but I get the following massage. Error: Cannot install 'libqt4-core. I have tried install libqt4-core it will not install.

---

### Post by stlsaint on 2009-09-02
have you tried via terminal or synap? try both ways and post what error your getting thats keeping you from installing it!

---

### Post by gmarcotte on 2009-10-13
I have ubuntu 9.04 and was trying to install skype-ubuntu-hardy_2.1.0.47-1_386.deb and got the same message about libqt4-core

somewhere in this somewhere eles on this form:

edit the /etc/apt/source.list file
there are some repos that are commented out so I uncommented them out:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse


after that I did a 
sudo apt-get upgrade; apt-get dist-upgrade

then I installed the skype package and this time it did it.

---

