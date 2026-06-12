---
title: "Broken packages/Unmet dependencies problems"
date: 2008-10-16
forum: General Help
---

### Post by AN@S on 2008-10-16
Hello, 

I don't fully understand the cause of this problem so I'll try to explain what happened with me. The problem is related to broken Compiz packages or something. This all started with Emerald where my windows decoration suddenly disappeared, I had to run 'emeral --reload' every time to fix this. Then I noticed that when Ubuntu notifies me of new updates that Compiz updates are kept not updated so I have to do a 'Partial Update'.
Today I followed [this tutorial]("http://www.debian-administration.org/articles/69") and did this:

```
apt-get dist-upgrade
```

This fixed the problem of "kept back" packages and I was able to do a full update this time, but I lost Compiz and all related packages.

When I try:

sudo apt-get install compiz

```
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
  compiz: Depends: compiz-plugins but it is not going to be installed
          Depends: compiz-gnome but it is not going to be installed
          Depends: compiz-fusion-plugins-main (>= 0.7.7+git20080807) but it is not going to be installed
          Depends: compiz-fusion-plugins-extra (>= 0.7.7+git20080807) but it is not going to be installed
          Depends: libcompizconfig0 (>= 0.7.7+git20080807) but it is not going to be installed
E: Broken packages

```

Now I disabled Visual Effects and I'm unable to install Compiz. :confused:

Please help. Thanks

---

### Post by pedro_orange on 2008-10-16
Might sound a bit simple but have you tried doing a:

```
sudo apt-get remove compiz
```

And then trying to install it again?

You can also use dpkg -l and dpkg -r to list and remove applications. Check the dpkg manual.

---

### Post by AN@S on 2008-10-16
> **pedro_orange said:**
> Might sound a bit simple but have you tried doing a:

```
sudo apt-get remove compiz
```

And then trying to install it again?



Compiz is not installed at all:

```
sudo apt-get remove compiz

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by pedro_orange on 2008-10-16
Well if Compiz is not installed, how is Emerald supposed to work?

So you did a dist-upgrade? What version are you running now? Intrepid?

System > Administration > System Monitor.
Choose the first tab "System" and you'll see your kernel and ubuntu version.

I presume that you had some problems with emerald and compiz, and then the upgrade noticed them and removed them. I would suggest you remove all trace of them and try to re-install them.

Remember to apt-get update so you get the updates sources.list.

---

### Post by AN@S on 2008-10-16
> **pedro_orange said:**
> Well if Compiz is not installed, how is Emerald supposed to work?

So you did a dist-upgrade? What version are you running now? Intrepid?

System > Administration > System Monitor.
Choose the first tab "System" and you'll see your kernel and ubuntu version.

I presume that you had some problems with emerald and compiz, and then the upgrade noticed them and removed them. I would suggest you remove all trace of them and try to re-install them.

Remember to apt-get update so you get the updates sources.list.

Hi, 
Forget about Emerald it's not my problem now, I was just trying to describe how everything started. I'm on Hardy, Kernel 2.6.24-21-server (I'm on a laptop PC but installed the server kernel so my system can recognizes more than 3GB of RAM).

How would I remove all trace of the packages?

---

### Post by pedro_orange on 2008-10-16
dpkg -l will list all the applications you have installed on your box.
You can grep that, or pipe it into more/less.
dpkg -r <package-name>
will remove the package.

I'd look for compiz / emerald ones that are still hanging around.

You could also do a sudo apt-get update, to update your sources.list so you download the right packages, when it comes to reinstalling.

---

### Post by oldos2er on 2008-10-16
An@s, can you post the output of "cat /etc/apt/sources.list"?

---

### Post by AN@S on 2008-10-19
> **oldos2er said:**
> An@s, can you post the output of "cat /etc/apt/sources.list"?

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sy.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sy.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://sy.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy universe
deb http://sy.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sy.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://sy.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sy.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://sy.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://wine.budgetdedicated.com/apt hardy main

deb http://packages.medibuntu.org/ hardy free non-free
deb http://ppa.launchpad.net/intuitivenipple/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intuitivenipple/ubuntu intrepid main
deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/
```

---

