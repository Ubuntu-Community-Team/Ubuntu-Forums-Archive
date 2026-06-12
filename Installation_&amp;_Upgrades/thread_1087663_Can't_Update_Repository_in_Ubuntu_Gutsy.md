---
title: "Can't Update Repository in Ubuntu Gutsy"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by adesia81 on 2009-03-05
Hi all,
I'm using Ubuntu 7.10 Gutsy, I have a problem when trying to update my repository using apt-get update.

Below the result when i type apt-get update :

```
neptune31@ip-wan:~$ sudo apt-get update
[sudo] password for neptune31:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources                                        
Fetched 3B in 7s (0B/s)                                                                                  
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

Then i follow the command that suggested by the error log,
and here are the result for the dpkg --configure -a command:

```

neptune31@ip-wan:~$ sudo dpkg --configure -a
Setting up launchpad-integration (0.1.15) ...
/var/lib/dpkg/info/launchpad-integration.postinst: 6: pycentral: not found
dpkg: error processing launchpad-integration (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on launchpad-integration; however:
  Package launchpad-integration is not configured yet.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kontact:
 kontact depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kontact (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kget:
 kget depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kget (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsole:
 konsole depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing konsole (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of korn:
 korn depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing korn (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kspaceduel:
 kspaceduel depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kspaceduel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdegames1:
 libkdegames1 depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkdegames1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpercentage:
 kpercentage depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpercentage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of krdc:
 krdc depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing krdc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcvsservice0:
 libcvsservice0 depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libcvsservice0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kteatime:
 kteatime depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kteatime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfouleggs:
 kfouleggs depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 kfouleggs depends on libkdegames1 (>= 4:3.5.7); however:
  Package libkdegames1 is not configured yet.
dpkg: error processing kfouleggs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdemultimedia-kio-plugins:
 kdemultimedia-kio-plugins depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdemultimedia-kio-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkmime2:
 libkmime2 depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkmime2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kandy:
 kandy depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kandy (--configure):

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfloppy:
 kfloppy depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kfloppy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksysv:
 ksysv depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing ksysv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knotes:
 knotes depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knotes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kbounce:
 kbounce depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 kbounce depends on libkdegames1 (>= 4:3.5.7); however:
  Package libkdegames1 is not configured yet.
dpkg: error processing kbounce (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdenetwork-kfile-plugins:
 kdenetwork-kfile-plugins depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdenetwork-kfile-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-bin:
 kdebase-bin depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdebase-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kiten:
 kiten depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kiten (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kenolaba:
 kenolaba depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 kenolaba depends on libkdegames1 (>= 4:3.5.7); however:
  Package libkdegames1 is not configured yet.
dpkg: error processing kenolaba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of superkaramba:
 superkaramba depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing superkaramba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmailcvt:
 kmailcvt depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kmailcvt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of knetworkconf:
 knetworkconf depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing knetworkconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdat:
 kdat depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kppp:
 kppp depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kppp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ksayit:
 ksayit depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing ksayit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of klines:
 klines depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 klines depends on libkdegames1 (>= 4:3.5.7); however:
  Package libkdegames1 is not configured yet.
dpkg: error processing klines (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpdf:
 kpdf depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpdf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kbattleship:
 kbattleship depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 kbattleship depends on libkdegames1 (>= 4:3.5.7); however:
  Package libkdegames1 is not configured yet.
dpkg: error processing kbattleship (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libktnef1:
 libktnef1 depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libktnef1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpf:
 kpf depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of konsolekalendar:
 konsolekalendar depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 konsolekalendar depends on libktnef1 (>= 4:3.5.7); however:
  Package libktnef1 is not configured yet.
dpkg: error processing konsolekalendar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplot:
 kmplot depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kmplot (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdeaddons-kfile-plugins:
 kdeaddons-kfile-plugins depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdeaddons-kfile-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpager:
 kpager depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkonq4:
 libkonq4 depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing libkonq4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelirc:
 kdelirc depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdelirc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdnssd:
 kdnssd depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kdnssd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpersonalizer:
 kpersonalizer depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kpersonalizer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kiconedit:
 kiconedit depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kiconedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kview:
 kview depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kate:
 kate depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kate (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ktuberling:
 ktuberling depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
 ktuberling depends on libkdegames1 (>= 4:3.5.7); however:
  Package libkdegames1 is not configured yet.
dpkg: error processing ktuberling (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kfax:
 kfax depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kfax (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kcron:
 kcron depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kcron (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmag:
 kmag depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing kmag (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of librss1:
 librss1 depends on kdelibs4c2a (>= 4:3.5.7-1); however:
  Package kdelibs4c2a is not configured yet.
dpkg: error processing librss1 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted
neptune31@ip-wan:~$ 

```

Can someone help me to solve my problem, thx before...

---

### Post by zvacet on 2009-03-05
I don´t know how to help you,because it is look like 

> These are the Ubuntu security notices that affect the current supported releases of Ubuntu 

Package you need for configure (kdelibs4c2a) is from security repo.

---

