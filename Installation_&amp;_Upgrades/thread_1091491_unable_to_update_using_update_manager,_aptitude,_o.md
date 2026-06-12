---
title: "unable to update using update manager, aptitude, or synaptic"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by pjizz on 2009-03-09
I have been completely unable to update my intrepid lappy for sometime now.  I have looked around for fixes but everything I find seems tailored to specific cases and I'm unable to successfully apply a given fix to my situation.  I'll try to give all relevant information...all help greatly appreciated

```
root@bander-laptop:/home/bander# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  g++: Depends: g++-4.3 (>= 4.3.1-1) but it is not installed
  swfdec-mozilla: Depends: libswfdec-0.8-0 but it is not installed
E: Unmet dependencies. Try using -f.
root@bander-laptop:/home/bander# 

```

```
root@bander-laptop:/home/bander# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstdc++6-4.3-dev g++-4.3 g++ flashplugin-nonfree
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  g++-4.3 libc6 libc6-dev libstdc++6-4.3-dev libswfdec-0.8-0
Suggested packages:
  g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg glibc-doc libc6-i686
  manpages-dev libstdc++6-4.3-doc
The following NEW packages will be installed:
  g++-4.3 libc6-dev libstdc++6-4.3-dev libswfdec-0.8-0
The following packages will be upgraded:
  libc6
1 upgraded, 4 newly installed, 0 to remove and 54 not upgraded.
22 not fully installed or removed.
Need to get 0B/13.7MB of archives.
After this operation, 33.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't locate auto/POSIX/autosplit.ix in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/AutoLoader.pm line 186.
 at /usr/lib/perl/5.10/POSIX.pm line 9
debconf: Perl may be unconfigured (Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 142819 files and directories currently installed.)
Preparing to replace libc6 2.8~20080505-0ubuntu8 (using .../libc6_2.8~20080505-0ubuntu9_i386.deb) ...
Can't locate auto/POSIX/autosplit.ix in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/AutoLoader.pm line 186.
 at /usr/lib/perl/5.10/POSIX.pm line 9
Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/libc6_2.8~20080505-0ubuntu9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.8~20080505-0ubuntu9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@bander-laptop:/home/bander# 

```

Synaptic lists g++ and swfdec-mozilla as broken packages, and trying to use Synaptic to fix broken packages also results in error:
E: /var/cache/apt/archives/libc6_2.8~20080505-0ubuntu9_i386.deb: subprocess pre-installation script returned error exit status 2

All this has left me with a crippled system and frustrated brain.

---

### Post by Neo_The_User on 2009-03-09
Well I don't know how to help but try not logging into root and use sudo instead (for future reference as well)

---

### Post by kestrel1 on 2009-03-09
A bad idea to use the root account as suggested above, Use sudo instead.
Are you able to connect to the Internet OK from this machine?

---

### Post by pjizz on 2009-03-11
i usually don't go root but didn't know if that would result in anything different.  i am able to connect to the internet fine

---

### Post by kestrel1 on 2009-03-11
No it shouldn't give different results.Have you tried running```
sudo dpkg --configure -a
```
Also check that you haven't got anon-proxy installed. You check this out in synaptic.

---

### Post by pjizz on 2009-03-11
tried that before, this is the result.  also, anon-proxy isn't installed (thankfully, as if it were synaptic wouldn't be able to remove it anyway)

i'm not too familiar with this stuff, but just from reading the output, it looks like I'm having some circular/iterated definition problems, one thing can't be done because another thing hasn't already been done, which in turn can't be done b/c another...

what to do what to do

```
bander@bander-laptop:~$ sudo dpkg --configure -a
[sudo] password for bander: 
Setting up dictionaries-common (0.98.14ubuntu1~intrepid1) ...
Can't locate auto/POSIX/autosplit.ix in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl/5.10/AutoLoader.pm line 186.
 at /usr/lib/perl/5.10/POSIX.pm line 9
Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing dictionaries-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on openoffice.org-common (>> 1:3.0.1); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-binfilter:
 openoffice.org-filter-binfilter depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-core (>> 1:2.3.0~oog680m1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-emailmerge:
 openoffice.org-emailmerge depends on python-uno; however:
  Package python-uno is not configured yet.
dpkg: error processing openoffice.org-emailmerge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.0.1-1ubuntu1~intrepid1); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dictionaries-common
 openoffice.org-common
 openoffice.org-style-human
 openoffice.org-java-common
 openoffice.org-officebean
 openoffice.org-base
 openoffice.org-core
 openoffice.org-draw
 openoffice.org-filter-mobiledev
 openoffice.org-calc
 openoffice.org-filter-binfilter
 openoffice.org-report-builder-bin
 openoffice.org-base-core
 openoffice.org-writer
 python-uno
 openoffice.org
 openoffice.org-emailmerge
 openoffice.org-impress
 openoffice.org-math

```

---

### Post by kestrel1 on 2009-03-12
It looks like it is to do with OpenOffice 3. Have you got the following line in your sources.list:```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
You can check this with```
gedit /etc/apt/sources.list
```
If so, coment it out so that it looks like this```
##deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
and try updating again.

---

### Post by pjizz on 2009-03-12
don't have the office pkg in ...have repos listed for do, last.fm, and a rhythmbox mod...but have had them turned off for a while b/c they haven't been updated.  apt doesn't work with these commented out or not.

---

### Post by kestrel1 on 2009-03-12
Can you post the output of your sources.list```
gedit /etc/apt/sources.list
```

---

### Post by pjizz on 2009-03-12
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.osuosl.org/ubuntu/ intrepid main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.osuosl.org/ubuntu/ intrepid-updates main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.osuosl.org/ubuntu/ intrepid universe
deb http://ubuntu.osuosl.org/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.osuosl.org/ubuntu/ intrepid multiverse
deb http://ubuntu.osuosl.org/ubuntu/ intrepid-updates multiverse

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
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://ubuntu.osuosl.org/ubuntu/ intrepid-security main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ intrepid-security restricted main multiverse universe #Added by software-properties
deb http://ubuntu.osuosl.org/ubuntu/ intrepid-security universe
deb http://ubuntu.osuosl.org/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main
deb http://apt.last.fm/ debian stable
deb http://blog.blackdown.de/static/debian/rhythmbox/ intrepid main
deb-src http://blog.blackdown.de/static/debian/rhythmbox/ intrepid main
```

---

### Post by pjizz on 2009-03-13
i could always do a fresh install...but that would be no fun at all

huzzah for iambic quadrameter!

---

