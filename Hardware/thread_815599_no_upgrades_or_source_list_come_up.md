---
title: "no upgrades or source list come up"
date: 2008-06-01
forum: Hardware
---

### Post by Ericwt on 2008-06-01
Here is my source list I can not add remove or update. I also can not see the source list to edit it package manager just hangs then dumps back to desk top. I hope someone can see something wrong so I can correct it.
Thanks Eric
Source list

# 
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [ftp://us.archive.ubuntu.com/ubuntu/](ftp://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [ftp://archive.canonical.com/ubuntu](ftp://archive.canonical.com/ubuntu) hardy partner
# deb-src [ftp://archive.canonical.com/ubuntu](ftp://archive.canonical.com/ubuntu) hardy partner

deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) hardy-security universe
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by overdrank on 2008-06-01
Hi and could you post the output of updating via the terminal
```
sudo apt-get update
sudo apt-get upgrade
```
Do you get any errors opening synaptic manager or add and remove?

---

### Post by Ericwt on 2008-06-02
> **overdrank said:**
> Hi and could you post the output of updating via the terminal
```
sudo apt-get update
sudo apt-get upgrade
```
Do you get any errors opening synaptic manager or add and remove?

Tried That can get updates that way but my problem is can not open package manager source list or add and remove programs. Try's to open then dumps back to desktop. This is on my work laptop and all this will work on desktop computer. There must be a simple reason why nothing works.
Eric

---

### Post by cjazz on 2008-06-02
Is your source list located in /etc/apt/sources.list? What happens if you try to open the file with:

```
gksudo gedit /etc/apt/sources.list
```?

It may not make any difference, but my sources.list file has http everywhere yours has ftp. Just wondering.

---

### Post by Ericwt on 2008-06-02
> **cjazz said:**
> Is your source list located in /etc/apt/sources.list? What happens if you try to open the file with:

```
gksudo gedit /etc/apt/sources.list
```?

It may not make any difference, but my sources.list file has http everywhere yours has ftp. Just wondering.

cjazz
I tried that change back from ftp to http same problem. I checked the source list on my desktop computer they are the same. 
On my desktop I can go to etc/apt/sources non root and double click on the source list it asks for a password for root. I then can see all options for software sources. On the laptop it just hangs for a while and stops.
Is there a way I could correct this using live cd or install cd.
Thanks Eric

---

### Post by cjazz on 2008-06-03
Maybe I'm not understanding you. My question is, what happens if you open a terminal and enter

gksudo gedit /etc/apt/sources.list

---

### Post by Ericwt on 2008-06-03
> **cjazz said:**
> Maybe I'm not understanding you. My question is, what happens if you open a terminal and enter

gksudo gedit /etc/apt/sources.list

Jazz 

gksudo gedit /etc/apt/source.list works in fact I changed my source list to http: from ftp that I had tried.

Heres what is happening 
I have updates ready for download right now. I click on the icon in the panel and update manager comes up. I try to install them and it just hangs till I kill and end it. Same if I try to use source list and synaptic package manager. Never asks for my root password if that helps.
I can use sudo apt-get update
sudo apt-get upgrade 
and I can download and install all updates.

Thanks for your help this must be something simple.
Eric

---

### Post by cjazz on 2008-06-04
Thanks for explaining. Sorry I didn't understand your problem before.

You might want to try running update-manager from a terminal and seeing if the output there gives you any clues. I'm assuming that your user account has full administration privileges. You can check through System>Administration>Users and Groups.

---

### Post by Ericwt on 2008-06-04
I ran in terminal and this is only thing I cansee wrong.
Sudo apt-get update
sudo:unable to resolve host harry
eric@harry

Then will fetch updates but will not upgrade 

Ready to start over 
Eric and thanks for your help you guys are great.

---

### Post by formol on 2008-06-04
hello

i've the same problem :

result from apt-get update:

sudo: unable to resolve host formol-desktop

---

### Post by Ericwt on 2008-06-06
Thanks to all that tried to help I am going to reformat and start from scratch. I can not resolve this problem. I made some kind of mistake some where after I installed 8.0 hope I can avoid this in the future. Ran 7.04 and 7.10 with no problems.
Eric

---

