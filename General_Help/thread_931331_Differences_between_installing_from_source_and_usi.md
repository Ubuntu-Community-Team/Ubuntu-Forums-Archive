---
title: "Differences between installing from source and using apt-get?"
date: 2008-09-27
forum: General Help
---

### Post by ldfj3jf on 2008-09-27
Hi, 

So I understand that since all computers are different, packages have to be installed from source. But - what I don't get - is how can apt-get work then, since it just seems to be downloading binaries?

Any pointer would be much appreciated!

---

### Post by ashmew2 on 2008-09-27
As far as I know , Compiling from source is because systems are different in the following aspects :

1) Linux Version (Ubuntu , Mandrake , RedHat , etc , etc) , to make it Linux-flavour independent.
2) Architecture : 32 Bit , 64 Bit .

Apt-get is configured according to the points mentioned above as well.. But since apt-get knows that its a Debian System and all Debian systems can run .deb files . it jst downloads the debs to a folder on ur root file system and installs them after that. 

As far as the architecture is concerned . it depends on which version you installed..If u installed Ubuntu 32 Bit , you'll have the 32 Bit repositories and so apt-get will download from them..Ull have 64 Bit repos in a 64 Bit install tho :)

---

### Post by phidia on 2008-09-27
> **ldfj3jf said:**
> Hi, 

So I understand that since all computers are different, packages have to be installed from source. But - what I don't get - is how can apt-get work then, since it just seems to be downloading binaries?

Any pointer would be much appreciated!

Although there are some distos that do install from source most don't.
There are exceptions to how package managers do what they do but generally a distro's package manager recognizes a particular file type (tgz for slackware, deb for debian and debian based, ect) and installs that.

You may want to read the wiki article on [linux package management]("http://en.wikipedia.org/wiki/Package_management_system") too.

---

### Post by jimmy the saint on 2008-09-27
You also recieved help in the identical post you made in the Beginner Talk.  Please don't double post.

---

