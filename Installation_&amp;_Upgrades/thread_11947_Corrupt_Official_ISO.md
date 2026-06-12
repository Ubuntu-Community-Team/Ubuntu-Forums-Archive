---
title: "Corrupt Official ISO?"
date: 2005-01-20
forum: Installation &amp; Upgrades
---

### Post by coldcoldcold on 2005-01-20
I've recently downloaded the warty-release-install-i386.iso from the official links from

[http://www.ubuntulinux.org/download](http://www.ubuntulinux.org/download)

I downloaded the iso from both the United Kingdom mirror and the Midwest United States mirror.  Ive also downloaded the iso from this mirror:

[http://ftp.cs.umn.edu/pub/ubuntu-releases/warty/](http://ftp.cs.umn.edu/pub/ubuntu-releases/warty/)

I compared the generated hash from my downloaded iso to the hashes listed at

[http://releases.ubuntu.com/warty/MD5SUMS](http://releases.ubuntu.com/warty/MD5SUMS)

the hashes matched perfectly.

however, upon burning and attempting to install i ran into many errors.  including this one:

grep /cdrom/dists/Stable/release/ not a directory

so, using a mandrake install i ran md5sum -c md5sum.txt to make sure that all the files were correct on the cd.

It turns out that 18 files inside the iso (all found in the /dists folder) are corrupt.
4 files, each 0kb in size, are supposed to be folders:
/dists/local
/dists/stable
/dists/testing
/dists/unstable

I've verified that these files are corrupt within the iso (by using winISO and nero) and on the cd by looking at them in My Computer on windows xp and through the console on a mandrake install.

any ideas on how to get past this problem?

---

### Post by coldcoldcold on 2005-01-20
nevermind.  ive figured it out.  for some stupid reason you can not have the dvd drive in the modular bay.  you HAVE to have the floppy disk module instaled.  you cant even have the modular bay empty.

hope that helps someone in the future with an inspiron 8000

---

