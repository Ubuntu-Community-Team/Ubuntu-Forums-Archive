---
title: "Synaptic Manager obstacle...help!"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by TheKahuna on 2009-09-05
Dear Friends:

Please help me...

I keep getting this when I go to update:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/B]
What do I do?

Aloha and Mahalo for your help

Warmly,

The Big Kahuna:)

---

### Post by pastalavista on 2009-09-05
> **TheKahuna said:**
> Dear Friends:

Please help me...

I keep getting this when I go to update:

**E: dpkg was interrupted, [COLOR="Red"][B]you must manually run 'dpkg --configure -a' to correct the problem**[/COLOR]. 
E: _cache->open() failed, please report.
[/B]
What do I do?

Aloha and Mahalo for your help

Warmly,

The Big Kahuna:)Open a terminal (Applications > Accessories > Terminal) and enter this:```
sudo dpkg --configure -a
```

It will ask for your password and no text or markers will appear when you type it but it will recognize and allow you to run the dpkg command with administrator privileges.

---

### Post by megahead on 2009-09-09
Hello,
I have the problem with my Synaptic Package Manager. When I try to open Synaptic Package Manager I get this message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried to command : sudo dpkg --configure -a
and after that I get this message:

edin@edin-laptop:~$ sudo dpkg --configure -a
[sudo] password for edin: 
Setting up sun-java6-doc (6-14-0ubuntu1.9.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by Partyboi2 on 2009-09-09
Download the Java Se Documentation from [[COLOR=Blue]here[/COLOR]]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jdk-6u10-docs-oth-JPR@CDS-CDS_Developer") to your Desktop. Then open a terminal and change to the Desktop Directory
```
cd ~/Desktop
```
Then change the permissions of the downloaded zip file with
```
 sudo chown root:root jdk-6u10-docs.zip
```
then copy it over to the /tmp directory
```
sudo cp jdk-6u10-docs.zip /tmp
```
then
```
sudo dpkg --configure -a
```

---

### Post by megahead on 2009-09-09
I followed your instructions and I got this:


edin@edin-laptop:~$ cd ~/Desktop
edin@edin-laptop:~/Desktop$ sudo chown root:root jdk-6u10-docs.zip
[sudo] password for edin: 
edin@edin-laptop:~/Desktop$ sudo cp jdk-6u10-docs.zip /tmp
edin@edin-laptop:~/Desktop$ sudo dpkg --configure -a
Setting up libc6 (2.9-4ubuntu6) ...

Setting up sun-java5-doc (1.5.0-18-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


And I got the same message like before : dkpg was interrupted....

Is there any solution :(

---

### Post by no2498 on 2009-09-09
take the 1 that dont update out of the repose
an run it again

---

### Post by megahead on 2009-09-09
> **no2498 said:**
> take the 1 that dont update out of the repose
an run it again
Sorry, but I don't understand what do you want to say.

---

### Post by megahead on 2009-09-09
I figure out. It is working now. 
I just did everything in the same way, just with different package (jdk-1_5_0-doc.zip).
Thank you guys (no2498 and Partyboi2)

---

### Post by drewphilipbarlow on 2009-09-09
hey guys. I've just started to use ubuntu, and still learning my way around. I attempted to install ePSXE through terminal, but now my app manager wont load. heres the error message.

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

synaptic wont open either...

"E: Malformed line 50 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report."

I opened gedit, blocked line 50, nothing, restored a backup, still nothing. opened natilus with sudo, checked the permissions, still nothing. I'm to new to really have any amazing brainwaves. heres the content of the file.

--------

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu](http://ppa.launchpad.net/moovida-packagers/ppa/ubuntu) jaunty main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main
deb [http://packages.dfreer.org](http://packages.dfreer.org) gutsy main

-----------------------------

are there sites where I can just download a fresh file?



!!!!
No worries, just worked it out, was a repository line that was slightly messed up. All fixed. After 14 years of windows, Linux is a whole new language, but its easier on the tongue.

---

