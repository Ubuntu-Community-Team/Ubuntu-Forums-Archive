---
title: "sudo apt-get dist-upgrade doesn't work"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by ubuntuforums on 2009-04-23
Hi I'm trying to upgrade my server from 8.10 to 9.04 through ssh, but when I enter in: sudo apt-get update, then sudo apt-get dist-upgrade, it says '0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.'

Anyone know what to do?

edit: 
my /etc/apt/sources.list:
```
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates universe

deb http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

---

### Post by daboroe on 2009-04-23
sudo apt-get update and
sudo apt-get upgrade-dist or sudo apt-get upgrade -d i thought

that is what i thought it was. i could be wrong

---

### Post by fusa on 2009-04-23
I was having the same problems from command line, then tried System>Administration>Update Manager.  There is a box near the top stating a new distribution is available.  Its going painfully slow with lots of errors downloading so might end up waiting a while.

---

### Post by leandromartinez98 on 2009-04-23
apt-get dist-upgrade  will not upgrade the distribution, it will upgrade the packages of the current distribution:

from man apt-get:

       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.

I think this is the way to upgrade the distribution, but before doing that I would wait for the advice of someone else:

[http://geekzine.org/2008/11/01/upgrade-your-ubuntu-server-to-intrepid-810/](http://geekzine.org/2008/11/01/upgrade-your-ubuntu-server-to-intrepid-810/)

There is another site explaining the same:

[http://www.cyberciti.biz/faq/howto-upgrade-ubuntu-servers-804-to-810/](http://www.cyberciti.biz/faq/howto-upgrade-ubuntu-servers-804-to-810/)

---

### Post by jeff.jones.illinois on 2009-04-23
Does anybody know if you already have the new 9.04 version ISO file burned to a CD how to upgrade from 8.10 to 9.04 using the files on a CD vs. having to use the online mirrors? Update Manager seems to only allow you to connect via the Internet to pull the new updates...I already have them burned on CD. Thanks.

---

### Post by fusa on 2009-04-23
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) has directions on upgrading from CD.

---

### Post by hiec on 2009-04-23
You can upgrade all your packages to the Jaunty version if you add the Alternate install CD to your package repositories in Synaptic. Maybe Update-manager then loads the packages from the CD instead of from the internet? I'm quite new to Linux, so I could be wrong though.

---

### Post by ubuntuforums on 2009-04-23
@leandromartinez98: That got it working.

1. Run: *apt-get install update-manager-core*

2. Then: *nano /etc/update-manager/release-upgrades*

2.1. Change *Prompt=lts* to [I]Prompt=normal
[/I]
3. Finally run: *do-release-upgrade*


The update is currently running, unfortunately going quite slow though (50KB/s). Thanks to everyone who replied. :)

---

### Post by ubuntuforums on 2009-04-23
So I finished the upgrade, everything was working well, then I rebooted my server, and it never started back up (tried multiple times). So unfortunately my host does not yet have a 9.04 template available just yet, so I'm going to install 8.10 again then upgrade to 9.04 immediately after, hopefully it will be okay. :/

---

### Post by Teatro on 2009-04-24
I went to the link fusa posted. It tells me I have to install all updates to 8.10 before upgrading to 9,04 via a disk image. This strikes me as, well, insane, but I started the process. Unfortunately, it threatens to take a couple of hours. The download is hovering at about 45 kb/s, despite my cable connection. Is this a traffic problem with the upgrade servers? Anyway, this is not as bad as the two and half days at 17 kb/s I was looking at before, but it's pretty unwieldy.

---

### Post by Sef on 2009-04-24
> Hi I'm trying to upgrade my server from 8.10 to 9.04 through ssh, but when I enter in: sudo apt-get update, then sudo apt-get dist-upgrade, it says '0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.'


You should not upgrade that way.   Only the recommended ways from the link in Post #6.

---

### Post by capitales7 on 2009-05-11
> **ubuntuforums said:**
> @leandromartinez98: That got it working.

1. Run: *apt-get install update-manager-core*

2. Then: *nano /etc/update-manager/release-upgrades*

2.1. Change *Prompt=lts* to [I]Prompt=normal
[/I]
3. Finally run: *do-release-upgrade*


The update is currently running, unfortunately going quite slow though (50KB/s). Thanks to everyone who replied. :)

YAY! :D
Just hope I don't kill my system.

---

