---
title: "Software Sources don't run on my Ubuntu 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by fantomatico on 2009-11-02
Hi there,

I've recently installed Ubuntu on my Compaq Presario CQ61 and everything runs smooth, except for Software Sources configuration.

I go to *System > Administration > Software Sources *and nothing happens. It doesn't run. It started happenig after I added a repository for Cinelerra from [here]("http://cinelerra.org/getting_cinelerra.php").


Can anyone help me?


Thanks

---

### Post by cariboo on 2009-11-02
What happens if you comment out the one repository? To do this open the /etc/apt/sources.list with gedit, press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

Just put a # in front of the offending repository and try running Software Sources again.

---

### Post by fantomatico on 2009-11-02
With offending repository do you mean the repository causing the problem?

I had already removed celerra repository via Synaptic.

This is what I get on /etc/apt/sources.list

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main universe

---

### Post by cariboo on 2009-11-03
There two things you can try, Press alt-F2 and type:

```
gksu /usr/bin/software-properties-gtk
```

to see if Software Sources starts, or go to System-->Administration-->Synaptic Package Manager-->Settings and make your changes there. It may be a problem with the mirror you are using so under the server setting select other, then click the select best server button.

---

### Post by Magmarules on 2009-11-11
so everything works? Compiz , microphone, etc..

---

### Post by gordintoronto on 2009-11-30
Cariboo907, I'm having exactly the same problem.  When I run the code you suggested, I get:

```

Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=data_dir, options=options, file=file)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 75, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 83, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 521, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```

In Synaptic, if I click on Settings/Repositories, there is a very short delay, and nothing happens -- so I can't change my server.

---

### Post by drfox on 2009-12-11
Go into Synaptic and search for software-properties-gtk, or software-properties-kde if you're running Kubuntu
Mark for complete removal. You'll be able to change your repos in Synaptic, but you won't be able to use Administration:Software Sources. 
Must be some sort of bug

HTH, Larry

---

### Post by unix1adm on 2009-12-17
I have this same problem on a new install. I cannot even run the commands you mention above. 

I canot run 
System-->Administration-->Synaptic Package Manager
or
ystem > Administration > Software Sources

It looks like it is starting on th ebottom of th escreen but nothing every shows up. 

I too run apt-get update but nothing gets updated and I know for sure there are updates out there as its a new build and there are always updates.

---

### Post by unix1adm on 2009-12-17
Its odd now it shows that I have 196 files to updat ebut when I select update it wont update the files. Does not ask me for my root passwd either.

---

