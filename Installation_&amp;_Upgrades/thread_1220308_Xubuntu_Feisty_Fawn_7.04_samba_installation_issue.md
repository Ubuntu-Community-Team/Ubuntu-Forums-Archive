---
title: "Xubuntu Feisty Fawn 7.04 samba installation issue"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by jwg89 on 2009-07-22
Guys,

Running on an old Dell Dimension 4600 Desktop.  Installed Xubuntu Feisty Fawn 7.04.

I've been having a lot of trouble (several days worth to be exact), trying to find a solution to this problem.  The fact that I'm a complete beginner doesn't help in this regard.  My issue is as follows:

I can't install the samba package.  I'm trying to turn my old computer into a server, but I can't seem to locate the samba package.  In synaptics, when I search for samba, all i come up with is libsmbclient, smbclient, and samba-client, all already installed.  When I enter the terminal, and enter "sudo apt-get install samba" I receive:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  smbclient samba-common
E: Package samba has no installation candidate




When I enter "sudo apt-get update" I receive a million lines, the latter portions giving me "failed to fetch" or "package 404 not found."  That part ends with:  
E: Some index files failed to download, they have been ignored, or old ones used instead.

I have also checked the repositories, and even edited the repository log file.  I have also tried enter "sudo apt-get install samba smbfs."  

I've researched this a ton, literally scouring internet forums, but I haven't seen a solution that I can understand, or that doesn't just point to the samba how-to install guide, which isn't helpful either.  I need clear, dumbed down instructions, otherwise I won't understand what I'm supposed to do to fix it.  Thanks in advance.

---

### Post by Rocket2DMn on 2009-07-22
Feisty Fawn is no longer supported, it reached End of Life almost a year ago.  This means that the repositories are no loger available.  You need to download a supported version of Ubuntu.  The latest is 9.04 Jaunty Jackalope, and the latest LTS (long term support) release is 8.04 Hardy Heron.  You can download them here - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

