---
title: "Help installing Avant-Window-Navigator"
date: 2008-09-28
forum: General Help
---

### Post by snkngshps on 2008-09-28
I was following [this guide]("http://qtbackup.quicktweaks.com/2008/04/three-little-things-to-make-your-ubuntu-desktop-beautiful-and-productive/") to install AWN. I had it in the past but after seeing all of the applets that could be added I thought I'd give it a shot again. So I used terminal to install AWN and the manager without any problems. But then the next steps have me install some software sources and run these commands:

*sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr*

Here is the output of what happened:
```
joshua@SNKNGSHPS:~$ sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libawn0-bzr libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common
  libgdl-gnome-1-0 python-awn-bzr python-gnome2-extras
Suggested packages:
  libgda3-freetds libgda3-mysql libgda3-odbc libgda3-postgres libgda3-sqlite
  python-gnome2-extras-dbg python-gnome2-extras-doc
Recommended packages:
  python-alsaaudio python-libgmail libgda3-bin
The following packages will be REMOVED:
  avant-window-navigator awn-manager libawn0 python-awn
The following NEW packages will be installed:
  avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr libawn0-bzr
  libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0
  python-awn-bzr python-gnome2-extras
0 upgraded, 11 newly installed, 4 to remove and 0 not upgraded.
Need to get 5239kB of archives.
After this operation, 24.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libawn0-bzr avant-window-navigator-bzr awn-core-applets-bzr python-awn-bzr
  awn-manager-bzr
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com hardy/main libgda3-common 3.0.2-2ubuntu1 [183kB]
Get:2 http://ppa.launchpad.net gutsy/main libawn0-bzr 0.3.1.bzr482.1~gutsy [81.5kB]
Get:3 http://ppa.launchpad.net gutsy/main avant-window-navigator-bzr 0.3.1.bzr482.1~gutsy [305kB]
Get:4 http://us.archive.ubuntu.com hardy/main libgda3-3 3.0.2-2ubuntu1 [431kB] 
Get:5 http://ppa.launchpad.net gutsy/main awn-core-applets-bzr 0.3.1.bzr866.1~gutsy [3740kB]
Get:6 http://us.archive.ubuntu.com hardy/main libgdl-1-common 0.7.11-1 [37.2kB]
Get:7 http://us.archive.ubuntu.com hardy/main libgdl-1-0 0.7.11-1 [74.7kB]     
Get:8 http://us.archive.ubuntu.com hardy/main libgdl-gnome-1-0 0.7.11-1 [5980B]
Get:9 http://us.archive.ubuntu.com hardy-updates/main python-gnome2-extras 2.19.1-0ubuntu7.1 [320kB]
Get:10 http://ppa.launchpad.net gutsy/main python-awn-bzr 0.3.1.bzr482.1~gutsy [21.5kB]
Get:11 http://ppa.launchpad.net gutsy/main awn-manager-bzr 0.3.1.bzr482.1~gutsy [40.3kB]
Fetched 5239kB in 15s (343kB/s)                                                
(Reading database ... 139131 files and directories currently installed.)
Removing awn-manager ...
Removing python-awn ...
Removing avant-window-navigator ...
Removing libawn0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libawn0-bzr.
(Reading database ... 139067 files and directories currently installed.)
Unpacking libawn0-bzr (from .../libawn0-bzr_0.3.1.bzr482.1~gutsy_i386.deb) ...
Selecting previously deselected package libgda3-common.
Unpacking libgda3-common (from .../libgda3-common_3.0.2-2ubuntu1_all.deb) ...
Selecting previously deselected package libgda3-3.
Unpacking libgda3-3 (from .../libgda3-3_3.0.2-2ubuntu1_i386.deb) ...
Selecting previously deselected package libgdl-1-common.
Unpacking libgdl-1-common (from .../libgdl-1-common_0.7.11-1_all.deb) ...
Selecting previously deselected package libgdl-1-0.
Unpacking libgdl-1-0 (from .../libgdl-1-0_0.7.11-1_i386.deb) ...
Selecting previously deselected package libgdl-gnome-1-0.
Unpacking libgdl-gnome-1-0 (from .../libgdl-gnome-1-0_0.7.11-1_i386.deb) ...
Selecting previously deselected package python-gnome2-extras.
Unpacking python-gnome2-extras (from .../python-gnome2-extras_2.19.1-0ubuntu7.1_i386.deb) ...
Selecting previously deselected package avant-window-navigator-bzr.
Unpacking avant-window-navigator-bzr (from .../avant-window-navigator-bzr_0.3.1.bzr482.1~gutsy_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/avant-window-navigator-bzr_0.3.1.bzr482.1~gutsy_i386.deb (--unpack):
 trying to overwrite `/usr/share/avant-window-navigator/active/glow3.png', which is also in package avant-window-navigator-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package awn-core-applets-bzr.
Unpacking awn-core-applets-bzr (from .../awn-core-applets-bzr_0.3.1.bzr866.1~gutsy_i386.deb) ...
Selecting previously deselected package python-awn-bzr.
Unpacking python-awn-bzr (from .../python-awn-bzr_0.3.1.bzr482.1~gutsy_i386.deb) ...
Selecting previously deselected package awn-manager-bzr.
Unpacking awn-manager-bzr (from .../awn-manager-bzr_0.3.1.bzr482.1~gutsy_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/avant-window-navigator-bzr_0.3.1.bzr482.1~gutsy_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

*** you can see towards the middle there is this little interesting section:
```
Removing awn-manager ...
Removing python-awn ...
Removing avant-window-navigator ...
Removing libawn0 ...
```

Sure enough, AWN was no longer on my computer. I tried to install it again but I keep getting this error.
```
joshua@SNKNGSHPS:~$ sudo apt-get install avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator: Depends: libawn0 (>= 0.2.6)
E: Broken packages

```

Anyone know what happened and how I can fix this?

---

### Post by Bakon Jarser on 2008-09-28
It says I don't have permission to access that guide.  How old is it?  It looks like you are using Gutsy (7.10), could the guide have been for a different version of Ubuntu?

---

### Post by Rayaz on 2008-09-28
If you are running hardy then you are using the wrong repositories! Have a look at this thread [http://ubuntuforums.org/showthread.php?t=733129&highlight=avant.I](http://ubuntuforums.org/showthread.php?t=733129&highlight=avant.I) followed it for setting up my AWN very easily.

---

### Post by snkngshps on 2008-09-28
I am running Hardy. The guide had two sources to add and both said gutsy but the guide said to add them for both gutsy and hardy. I'll try this guide out instead.

---

