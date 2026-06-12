---
title: "Can't install, repos gone."
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by Kvothe on 2009-10-21
I'm running Ubuntu Hardy (8.04.1). I changed my server setting under Synaptic repositories and the original server from Peru disappeared. I cannot install any packages. How would I go about fixing this? Sorry if this in the wrong section. Every time I try to install a program it gives me the error:

```
Package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package has no installation candidate
```

---

### Post by stlsaint on 2009-10-21
go back to your sources list gui and where you selected to change the server...choose the other option in the drop down box and find your server again.

---

### Post by Kvothe on 2009-10-21
It's not there. The Synaptic Update tray icon is gone as well, but that might not be relevant.

---

### Post by stlsaint on 2009-10-21
system>admin>software sources

thats not there?

---

### Post by PorkyPie on 2009-10-21
That's a bit odd. To get into Software Sources, try ALT+F2 and type

```
sudo software-properties-gtk
```Make sure you tick the "Run in Terminal" box, as you'll be prompted for your password. That should get you into Software Sources.

PS. You can also run this command in the Terminal (if it's there! ;)) Just forget about the "Run in Terminal" bit.

---

### Post by Kvothe on 2009-10-21
No no no, I can get to that, but the server isn't there. Where it now says "Server for United States", it used to say "Server for Peru". I go to look for individual servers in the "Other..." option and none for Peru come up. What mirror are you using? I'll see if that one works.

When I used that command, the program opened, but I got the warning:

```
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
```Again, might not be relevant.

---

### Post by Kvothe on 2009-10-26
Bump.

---

### Post by jheaton5 on 2009-10-26
In a terminal type ```
$ cat /etc/apt/sources.list
``` and post the results here.

---

### Post by jheaton5 on 2009-10-26
See [here]("https://help.ubuntu.com/community/SourcesList") and [here]("https://launchpad.net/ubuntu/+archivemirrors")

---

### Post by Kvothe on 2009-10-26
Here:
> # deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy main restricted
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-updates main restricted
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy universe
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy universe
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-updates universe
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy multiverse
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy multiverse
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-updates multiverse
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://pe.archive.ubuntu.com/ubuntu/](http://pe.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-security main restricted
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-security main restricted
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-security universe
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-security universe
deb [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-security multiverse
deb-src [http://mirror.fslutd.org/linux/distributions/ubuntu/packages/](http://mirror.fslutd.org/linux/distributions/ubuntu/packages/) hardy-security multiverse

---

