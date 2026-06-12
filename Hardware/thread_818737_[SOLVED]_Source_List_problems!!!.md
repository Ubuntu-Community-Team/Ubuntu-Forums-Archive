---
title: "[SOLVED] Source List problems!!!"
date: 2008-06-04
forum: Hardware
---

### Post by salihumon on 2008-06-04
Hi All,
First of all I wanna thank ubuntu_demon who helped me (in person) te resolve the problem with wireless configuration.


But now I have another problem with the source list, and I hope You somebody around will be able to help me.

Namely,I had problems with totem (it did not open some files), so I thought maybe the problem was because my graphic card was not enabled, when I checked @ System>Administration>Hardware drivers.

My Graphic card is NVIDIA GeForce Go 7300. 

In order to do that I tried to follow these instructions : [http://ubuntuforums.org/showthread.php?t=428317](http://ubuntuforums.org/showthread.php?t=428317) . But it turned to be a mistake. Because when I restarted my computer it said to chose the card, and I chose the type of my graphic card which is NVIDIA GeForce Go 7300, but the resolution was messed up, and I could not rearrange that. However I restarted once again in recovery option  and the resolution is back how it was (now it is OK) , but the card still seems to be disabled and I can not access anymore Applications > Add/Remove, When I try that , I get this message:

Failed to check for installed and available applications

> This is a major failure of your software management sustem. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/cources.list' and reload sotware information with: ' sudo apt-get update' and ' sudo apt-get install -f'

When I try those in Terminal I get this:

    > mon@mon-laptop:~$ sudo apt-get update
    [sudo] password for mon:
    E: Type 'sudo' is not known on line 62 in source list /etc/apt/sources.list
    mon@mon-laptop:~$ sudo apt-get install -f
    E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
    E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


In addition when I try to enable now the graphic card by System> Administration > Hardware Drivers and I try to enable it, I receive this message:
> 
    E: Type 'sudo' is not known on line 62 in source list /etc/apt/sources.list
    E: The list of sources could not be read.
    Go to the repository dialog to correct the problem.
    E: _cache->open() failed, please report.

And my source list looks like this :
> 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted main #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse










sudo apt-get update

cd
exit


If somebody can tell me what should I do , I would appreciate it.

Thank You in advance

---

### Post by ubuntu_demon on 2008-06-05
Hey,

I mailed this to you last week :

[quote=ubuntu_demon]
....remove any linux commands from your /etc/apt/sources.list which you
might have added to the end by accident. All lines should start with
either 'deb' or '#' (without the ' signs).....
[/quote]

Turns out you still had some commands in your sources.list. Please remove these commands from your sources.list

```

sudo gedit /etc/apt/sources.list

```
and remove this part :

```

sudo apt-get update

cd
exit 

```

Issue the following two commands. The first one goes to all url's of the sources list and downloads some information. It doesn't understand those commands you removed but now it is fixed. The second one is probably not needed but configures any unconfigured packages and doesn't do anything if there aren't any. 

```

sudo aptitude update
sudo dpkg --configure -a

```

To know more about these commands do :
```

man aptitude
man dpkg

```

The totem problem is probably unrelated. But let's try to solve that too. Try if the media file(s) play with vlc. If both totem and vlc don't play them you them then read the following post which contains more information about multimedia and also explains a little about medibuntu,w32codecs and mplayer. In general it's better not use unofficial repositories unless you trust them and really really need them :
[http://ubuntuforums.org/showthread.php?t=567507](http://ubuntuforums.org/showthread.php?t=567507)

I'm sure this solves your problems. Next time only follow instructions for Hardy and only if you exactly understand what you are doing. So look up the commands with man and/or read [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto) and/or ask in the thread.

Have fun with Ubuntu :)

---

### Post by salihumon on 2008-06-05
@ ubuntu_demon 

Thank You very much man , once again.

Yeah , the problem is resolved.Now if we want to meet again , we can do it just for a drink. Because there is no problem to resolve anymore.

See You,
mon

---

### Post by ubuntu_demon on 2008-06-05
> **salihumon said:**
> @ ubuntu_demon 

Thank You very much man , once again.

Yeah , the problem is resolved.Now if we want to meet again , we can do it just for a drink. Because there is no problem to resolve anymore.

See You,
mon
You are welcome. You may buy me a drink if you want :D

Using the non-free nvidia driver is only useful for 3d and desktop effects (compiz). The free software nv driver you are using works fine for normal desktop work.

---

