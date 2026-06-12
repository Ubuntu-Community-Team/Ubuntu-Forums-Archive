---
title: "synaptic repositories editor fails to start"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2009-09-10
Hello.  I'm having a problem in that my repositories editor in Synaptic fails to start.  I go Synaptic > Settings > Repositories, then there's a slight delay after which nothing happens.  I'll try reading the Synaptic manual, but I hope someone here might be able to help.

Here's some more info:  sudo apt-get update returns the following error
```
W: Failed to fetch http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/n/a/main/binary-amd64/Packages.gz  404 Not Found
```

Also sudo gedit /etc/apt/sources.list shows that the offending ppa.launchpad.net URL isn't even there.  ??
```
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

---

### Post by drs305 on 2009-09-10
Look for the file in the /etc/apt/sources.list.d  You can either delete it or rename it by changing the ending to something other than .list
```

gksudo nautilus /etc/apt/sources.list.d

```

That should let Synaptic run properly again. Then you can figure out what you want to do about that specific repository.

---

### Post by Nopposan on 2009-09-10
Thank you for your quick reply.

I did as you suggested, but the symptoms I described remain.  Does this help?
```
sudo software-properties-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.5/site-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 78, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.5/site-packages/softwareproperties/SoftwareProperties.py", line 516, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.5/site-packages/aptsources/distro.py", line 85, in get_sources
    "Error: could not find a distribution template")
aptsources.distro.NoDistroTemplateException

```

Then there's the fact that when I run lsb-release -a I get something bizarre that I posted elsewhere on the Ubuntu forums:
```
:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Debian
Description:	DebianEdu/Skolelinux (terra)
Release:	testing/unstable
Codename:	n/a

```

Could that have something to do with it?

---

### Post by Nopposan on 2009-09-10
Ahah.  Google is My Friend!

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513039]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=513039")

> The problem disappears when the missing URI is added to sources.list:

  deb http://<mirror>/debian lenny main

which was not included by D-I (because of install being networkless).

This requires editting sources.list by hand, which defeats the purpose of
providing software-properties-gtk.


However, I'm not sure if that repo actually ought to be added to my Ubuntu installation.  What's its equivalent?

---

### Post by Nopposan on 2009-09-10
There's also the message saying that I have 718 updates available?  But, when I run the update manager it tells me that the system is up to date.

See attachments.

Thanks.

---

