---
title: "Added &quot;opera&quot; repository, cant find it to install it in Synaptic..."
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by Mugzilla on 2009-02-19
I just did a fresh install of 8.10 64 bit on an IBM x61s.  I have had great success w/ 8.10 64 bit and opera on this machine in the past.
[B][SIZE="3"]
Here is the dilemma:[/SIZE][/B]

I added the repository Opera recommends to install their browser. 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

I also added this repository:

deb [http://deb.opera.com/opera](http://deb.opera.com/opera) intrepid non-free

I added the Opera GPG key for the 1st repo. 

When I search in Synaptic for OPERA, nothing shows up! I have installed opera using the shell

sudo apt-get update
sudo apt-get install opera

The conundrum:  Opera is installed.  It shows up under applications ->internet.  However, OPERA won't connect to the internet!  Firefox works just fine.
[B][SIZE="4"]
What I want to know:  

#1 How can I get OPERA to show up in synaptic pkg manager? 
#2 How can I get opera to connect to the internet?
#3 During install, opera recommended the following packages be installed also:[/SIZE][/B]

pdf-npapi-plugin 
djvulibre-plugin 
mozilla-acroread 
sun-java6-jre

sun-java5-jre 
java-gcj-compat 
xine-plugin 
gxineplugin 
mplayerplug-in

kaffeine-mozilla 
mozilla-mplayer 
mozilla-helix-player 
gecko-mediaplayer

mozplugger plugger mozilla-bonobo


 How do I install them w/o synaptic to tell me if there are other dependencies?

---

### Post by zika on 2009-02-19
>>deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
shouldn't there be intrepid instead of hardy  ^^^^ ... ?

---

### Post by Mugzilla on 2009-02-19
> **zika said:**
> >>deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
shouldn't there be intrepid instead of hardy  ^^^^ ... ?

I have [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner in there, as well as [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner (source code) in there too...

---

### Post by zika on 2009-02-19
> **Mugzilla said:**
> I have [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner in there too...
OK, then You do not need this line with "hardy" in it ... :)

---

### Post by Mugzilla on 2009-02-19
> **zika said:**
> OK, then You do not need this line with "hardy" in it ... :)

Here is what I have under 3rd party software...
archive.canonical.com/ubuntu intrepid partner
archive.canonical.com/ubuntu intrepid partner (source code)
deb.opera.com/opera/stable non-free
deb.opera.com/opera intrepid non-free


WHAT OTHER REPOS should I have?

---

### Post by Mugzilla on 2009-02-19
Another point of interest:  When I launch synaptic pkg mgr, and I click reload, I get this message:

[B][SIZE="2"]failed to fetch [http://deb.opera.com/opera/dists/intrepid/non-free/binary-amd64/Packages.gz](http://deb.opera.com/opera/dists/intrepid/non-free/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/SIZE][/B]

---

### Post by howefield on 2009-02-19
Paste your sources.list contents..

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by zika on 2009-02-19
I was just saying that having "hardy" repo in intrepid could be a call for trouble.
as long as I'm writing, check that opera-repo 'cause it is not valid, it seems ...
You can always check the repo by simply going there in Your browser ...

---

### Post by Mugzilla on 2009-02-19
> **howefield said:**
> Paste your sources.list contents..

```
gksudo gedit /etc/apt/sources.list
```

 deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) intrepid non-free

---

