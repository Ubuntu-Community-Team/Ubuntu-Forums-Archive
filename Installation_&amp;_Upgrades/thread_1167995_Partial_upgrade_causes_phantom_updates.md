---
title: "Partial upgrade causes phantom updates"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by wyhog on 2009-05-23
I have used Ubuntu since 6.06. I've had Ubuntu 8.04 since last Fall. It is set up to Update weekly. 

The May 9, 2009 update said it could not update and it needed to do a "partial upgrade" of 104MB. I let it do that and it said it was successful. I rebooted as it indicated and everything seems to work. EXCEPT that whenever I run Update Manager now it always says that there are 3 updates available totaling 28.5 MB. But there are no updates listed, just a blank area in the list box. If I tell it to go ahead and get and install these phantom "updates" it checks the system and then simply comes back as before stating there are three updates available totaling 28.5 MB but still lists none of them. 

I restored a hard disk image back to the May 03, 2009 state and every thing worked. But when I ran Update Manager I get the exact same thing again. It wants to do a Partial Upgrade of 104MB and it does it succesfully. But after that whenever I run Update Manager it gives me the constant "Three updates available" with none listed.
 
Help! How can I correct this?

Wyhog

---

### Post by taurus on 2009-05-23
Sounds like a there is a new kernel that your machine can upgrade to.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by wyhog on 2009-05-23
>sudo apt-get dist-upgrade

Is that going to upgrade me to 8.10 or higher? I want to stay with the 8.04 LTS version.

When Update Manager did the 104MB partial upgrade some of the things were linux-headers-2.6.24-24 plus all of the usual kernal stuff like: -generic, -image, -ubuntu-modules, -restricted-modules, all for 2.6.24-24

Wyhog

---

### Post by taurus on 2009-05-23
> **wyhog said:**
> >sudo apt-get dist-upgrade

Is that going to upgrade me to 8.10 or higher? I want to stay with the 8.04 LTS version.

No, it's not.

> When Update Manager did the 104MB partial upgrade some of the things were linux-headers-2.6.24-24 plus all of the usual kernal stuff like: -generic, -image, -ubuntu-modules, -restricted-modules, all for 2.6.24-24

Wyhog

You still have an option to back out if you run **sudo apt-get dist-upgrade** though.

---

### Post by wyhog on 2009-05-23
Ok I did both of the things you suggested. Here is what I got for the 
sudo apt-get dist-upgrade:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The Update Manager still shows Three updates available. 28.5MB total. But lists nothing.

Wyhog

---

### Post by taurus on 2009-05-23
Click the update manager icon and post a screenshot of it.

---

### Post by wyhog on 2009-05-23
[IMG]http://www.alkrug.vcn.com/tmp/updatemgr.png[/IMG]

Note that the Update Manager does still work. If there are any actual updates it will list them and install them. For instance this morning when I first checked there were two new updates and it listed the two in the list boxes. But at the top where it now says there are 3 updates it then said there were Five updates. In other words the count is always 3 above reality.

Wyhog

---

### Post by taurus on 2009-05-23
What does your /etc/apt/sources.list look like?

```
cat /etc/apt/sources.list
```

---

### Post by wyhog on 2009-05-23
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Wyhog

---

### Post by taurus on 2009-05-23
Make sure you have closed down update manager window first.  Then, post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by wyhog on 2009-05-23
sudo apt-get update
[sudo] password for xxxx:

Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Wyhog

---

### Post by taurus on 2009-05-23
Have you reboot your machine?

---

### Post by wyhog on 2009-05-23
Yes, two or three times today and every day since the May 9th partial upgrade that did this. The computer is turned off when not in use. One wonders where the Update Manager gets its count from since using apt-get directly seems to work ok without giving phantom updates. 

As I said above, I restored a May 03, 2009 hard drive image and Update Manager is ok there. But both times that I let it perform the partial upgrade it wanted to do, the result afterwards is the showing there are 3 phantom updates.

Wyhog

---

### Post by wyhog on 2009-05-24
I still have the problem. Anybody have any ideas?

I decided to see where the phantom updates are coming from. So I went to Software Sources and turned them all off then turned on one at a time. Each time I turned one source on I would let it reload the sources then I'd run Update Manager. I find that Update Manager is OK with only Canonical main, Universe, and Restricted checkmarked. I don't get the 3 phantom updates available message. But if I have Multiverse checkmarked in Software Sources then when I run Update Manager I do get the 3 phantom updates available message. So it appears that it is something in the Multiverse repository that is causing the problem in my system.

Wyhog

---

### Post by wyhog on 2009-06-07
I still have this problem and it is driving me nuts!

The active lines of my /etc/apt/sources.list file are:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main universe restricted multiverse

I can remove the word "multiverse" from the end of the last two lines and I still have the 3 phantom updates problem. But if I replace those words and then delete the word "multiverse" from the end of the first line, the problem is gone. Update Manager shows my system is up to date instead of showing there are 3 phantom updates available. At this point the active lines of my sources.list file are:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main universe restricted multiverse

Note that the word "multiverse" is not there for the first line only. If I put that word back in then I get the problem back.

Anybody with any ideas?
Where does Update Manager get its count of available updates? I assumed it got it from apt-get upgrade but apparently not because this is what I get.

root@myroom:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Wyhog

---

