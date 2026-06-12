---
title: "koffice / kthesaurus conflict"
date: 2005-12-03
forum: General Help
---

### Post by monkblah on 2005-12-03
Hi, I have kubuntu 5.10. I installed koffice via apt-get, which installed a bunch of packages. It tried to install kthesaurus as well, claiming it was required. But it could not actually complete the install since it seems that kthesaurus conflicts with koffice-data.

Now I am unable to install kthesaurus, and apt keeps complaining whenever it is run. It suggests I run , but that doesn't work, leaving me where I started. Can someone help me?

```
==================================================
$ sudo apt-get install xclip
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kword: Depends: kthesaurus but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
$
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  kthesaurus
Suggested packages:
  koffice-doc-html
The following NEW packages will be installed:
  kthesaurus
0 upgraded, 1 newly installed, 0 to remove and 442 not upgraded.
15 not fully installed or removed.
Need to get 0B/322kB of archives.
After unpacking 1171kB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 88439 files and directories currently installed.)
Unpacking kthesaurus (from .../kthesaurus_1%3a1.4.1-0ubuntu7_i386.deb) ...
Replacing files in old package koffice-libs ...
dpkg: error processing /var/cache/apt/archives/kthesaurus_1%3a1.4.1-0ubuntu7_i386.deb (--unpack):
 trying to overwrite `/usr/share/apps/thesaurus/thesaurus.txt', which is also in package koffice-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kthesaurus_1%3a1.4.1-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$
=================================================

```

---

### Post by mlomker on 2005-12-04
I think you'll need to use the --force options to either remove the thesarus or to install it, your choice.  Overwriting that one file shouldn't hurt anything, so:

```

sudo apt-get install --force-yes kthesaurus

```

---

### Post by monkblah on 2005-12-05
Hi, I tried to install using --force, but this is what I got:


```

$ sudo apt-get install --force-yes kthesaurus
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  koffice-doc-html
The following NEW packages will be installed:
  kthesaurus
0 upgraded, 1 newly installed, 0 to remove and 442 not upgraded.
15 not fully installed or removed.
Need to get 0B/322kB of archives.
After unpacking 1171kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 88439 files and directories currently installed.)
Unpacking kthesaurus (from .../kthesaurus_1%3a1.4.1-0ubuntu7_i386.deb) ...
Replacing files in old package koffice-libs ...
dpkg: error processing /var/cache/apt/archives/kthesaurus_1%3a1.4.1-0ubuntu7_i38                  6.deb (--unpack):
 trying to overwrite `/usr/share/apps/thesaurus/thesaurus.txt', which is also in                   package koffice-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kthesaurus_1%3a1.4.1-0ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

```

---

### Post by mlomker on 2005-12-05
I'm left to assume that file is corrupt.  I'd delete it.

```

sudo rm /var/cache/apt/archives/kthesaurus_1%3a1.4.1-0ubuntu7_i386.deb

```

---

### Post by monkblah on 2005-12-05
(Thanks for helping, mlomker) I deleted it, and tried to force apt-get kthesaurus again, but with the same result and message as before. Deost this mean the package in the ubuntu.com archive is corrupted? If so, whom should I report this to? Should I just give up on koffice and de-install its packages?

---

### Post by mlomker on 2005-12-06
[QUOTE=monkblah] If so, whom should I report this to? Should I just give up on koffice and de-install its packages?[/QUOTE]

Well, I have kthesaurus and koffice-data installed...they installed when I installed Koffice.  I'm not sure why you suffered the original problem.

What [repository]("http://www.ubuntuforums.org/showthread.php?t=74729") did you add to obtain Koffice?

---

### Post by monkblah on 2005-12-06
[QUOTE=mlomker]
What [repository]("http://www.ubuntuforums.org/showthread.php?t=74729") did you add to obtain Koffice?[/QUOTE]

I didn't need to add any, it just installed when I ran apt-get install.

This is my /etc/apt/sources.list:

```

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

#ubuntu plf packages [http://wiki.ubuntu-fr.org/doc/plf]
# for w32codecs & the like [ http://ubuntuforums.org/archive/index.php/t-79449.html]
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free




```

---

### Post by mlomker on 2005-12-06
Ok, it looks like they have them in the main repos now.  I installed them when it was first released and used the Koffice repository.

---

### Post by monkblah on 2005-12-07
I assume there is some problem with the koffice/kthesaurus packages that has been causing my troubles... if this is the case, to whom should I report it?

---

