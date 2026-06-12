---
title: "Can't Install FireFox?"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by antdgar on 2009-08-30
Ubuntu server 9.04

```
sudo apt-get install firefox-3.0
[sudo] password for antd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9.0.1) but it is not going to be installed
               Depends: libgtk2.0-0 (>= 2.16.0) but 2.14.5-1ubuntu2 is to be installed
E: Broken packages

```

---

### Post by Partyboi2 on 2009-08-30
Hi, can you post your sources.list
```
cat /etc/apt/sources.list
```

---

### Post by antdgar on 2009-08-30
yep:

```
# deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.1)]/ jaunty main restricted

#deb cdrom:[Ubuntu-Server 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb ftp://mir1.ovh.net/ubuntu/ jaunty main restricted
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://mir1.ovh.net/ubuntu/ jaunty-updates main restricted
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb ftp://mir1.ovh.net/ubuntu/ jaunty universe
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty universe
deb ftp://mir1.ovh.net/ubuntu/ jaunty-updates universe
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb ftp://mir1.ovh.net/ubuntu/ jaunty multiverse
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty multiverse
deb ftp://mir1.ovh.net/ubuntu/ jaunty-updates multiverse
deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb ftp://mir1.ovh.net/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src ftp://mir1.ovh.net/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by Partyboi2 on 2009-08-30
Your sources.list appears in order. Before trying to install firefox did you run
```
sudo apt-get update
```For some reason it looks like it is wanting to install a older version of libgtk2.0-0.

---

### Post by antdgar on 2009-08-31
> **Partyboi2 said:**
> Your sources.list appears in order. Before trying to install firefox did you run
```
sudo apt-get update
```For some reason it looks like it is wanting to install a older version of libgtk2.0-0.
I ran and installed updates after I installed the OS.
So it's not possible for me to install firefox? =[

---

### Post by QIII on 2009-08-31
If you want to attempt to fix the broken packages, you can do so from Synaptic (or from the command line.  But if you are new, I'd recommend Synaptic)

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

There is a section on how to fix broken packages.

---

### Post by running_rabbit07 on 2009-08-31
Follow the directions on this [how-to]("http://www.psychocats.net/ubuntu/firefox") and then you will have FF3.5 which is even better.

---

### Post by antdgar on 2009-09-03
> **running_rabbit07 said:**
> Follow the directions on this [how-to]("http://www.psychocats.net/ubuntu/firefox") and then you will have FF3.5 which is even better.

The link says "This command assumes you've downloaded the Firefox .tar.bz2 file to your home directory"

but doesn't give the link to the .tar.bz2 file?

---

### Post by wojox on 2009-09-03
Just open System > Administration > Synaptic Package Manager

Search firefox and install what version you want.

---

### Post by antdgar on 2009-09-03
> **wojox said:**
> Just open System > Administration > Synaptic Package Manager

Search firefox and install what version you want.
I don't have synaptic package manager or GNOME/KDE. I have fluxbox gui and XFCE4 desktop

---

### Post by bumanie on 2009-09-03
This should work, but I'm not sure why you want an old version. Best of luck.
> wget -P ~ [ftp://ftp.mozilla.org/pub/firefox/releases/3.0.9/linux-i686/en-US/firefox-3.0.9.tar.bz2](ftp://ftp.mozilla.org/pub/firefox/releases/3.0.9/linux-i686/en-US/firefox-3.0.9.tar.bz2) && tar xjf ~/firefox-3.0.9.tar.bz2 -C ~

---

### Post by antdgar on 2009-09-04
> **bumanie said:**
> This should work, but I'm not sure why you want an old version. Best of luck.
I dont want an old version. I just want any version which is easy to install :)

```
wget -P ~ ftp://ftp.mozilla.org/pub/firefox/re...-3.0.9.tar.bz2 && tar xjf ~/firefox-3.0.9.tar.bz2 -C ~ 
--2009-09-04 13:28:01--  ftp://ftp.mozilla.org/pub/firefox/re...-3.0.9.tar.bz2
           => `/home/antd/re...-3.0.9.tar.bz2'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/firefox ... done.
==> SIZE re...-3.0.9.tar.bz2 ... done.
==> PASV ... done.    ==> RETR re...-3.0.9.tar.bz2 ... 
No such file `re...-3.0.9.tar.bz2'.
```

---

### Post by bumanie on 2009-09-04
The code does work, but the forum box is shortening the command for some reason. Not sure how to stop it doing that - sorry I can't help it. I'll see if I can find where I got the code and send you the url. The code does work, I have used it.

This is not the exact thing I had before, but coming from 'ubuntu geek', it should work. Go [here]("http://www.unixmen.com/component/content/article/300?joscclean=1&comment_id=479") Hope this  works.

---

### Post by antdgar on 2009-09-04
Weird, the wget URL doesn't work for me.

Is there any other browser I can easily install?

---

