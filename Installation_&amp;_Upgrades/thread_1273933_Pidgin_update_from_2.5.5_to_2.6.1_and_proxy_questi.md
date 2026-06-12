---
title: "Pidgin update from 2.5.5 to 2.6.1 and proxy question"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by finmanrushfan on 2009-09-23
In trying to help a friend of mine configure his proxy settings for aim in Pidgin I noticed that he was running version 2.6.1 while I am only running 2.5.5. He does not remember doing anything to update it, although he may have done so without realizing it. When I run 

```
sudo apt-get install pidgin
```
I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

The way I understand it it takes a while after a new version of Pidgin is released to make its way into the update repositories, but judging by the fact that my friend is not sure how he got it, it seems as if 2.6.1 is currently the supported version. Is my understanding flawed in some way?

Also, my college's network is behind a proxy, and the aforementioned friend has had trouble getting pidgin to connect. As far as I can tell, all of his network settings within pidgin are the same as mine, yet he cannot connect to the aim server - are there any suggestions of where else I might look to see where his settings are different from mine?

---

### Post by rreese6 on 2009-09-24
Although it would have been nice to know if you both are running the same version and flavor of linux. If you are and you have done
these: 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install pidgin
```

on both machines, then I would suspect that he has another repository
that is feeding him the different version.
Uninstall his version, do the above and see if it comes back as 2.61 or not. if it does, compare your repositories (/etc/apt/sources.lst)
you can also use synaptic to look at that, it is just not as detailed.

Maybe once the versions are the same then you should have no problem connecting....of course there may be the possibility that his connection tot he University Network is limited and yours is not.
In that case you need to get a hold of the system admin and have them open the 5190 port for "AIM".

good luck and let me know if this helps any.

---

### Post by zeroseven0183 on 2009-09-24
I think Pidgin is no longer supported by Ubuntu. However, you can download an upgrade by doing the procedures mentioned in [Ubuntu Blog: Pidgin 2.6.1 is Out with Voice and Video Support]("http://www.ubuntu-inside.me/2009/08/pidgin-261-is-out-with-voice-and-video.html")

---

### Post by finmanrushfan on 2009-09-24
Both my friend and I are running Ubuntu 9.04 (he used the same CD as I did to install.) After un-installing pidgin and following your instructions - he gets 2.6.1 and I get 2.5.5. As far as I can tell, our repositories are the same, mine is
```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

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

and his is 

```
#deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

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

Apparently he entered some commands that he found on another forum (perhaps a pidgin forum of some sort?) which might explain how he ended up with a newer version.  Is there any way to completely remove all traces of the program in case there is something stored locally?

When I emailed the school's helpdesk, they told me to use server kdc.uas.aol.com and port 5190, however, the only way I have been able to connect is via login.messaging.aol.com and port 443.(on both pidgin and trillian in windows) Thanks for all of your help, and please let me know if you think of anything else for me to try.

---

### Post by zeroseven0183 on 2009-09-27
You can get an updated version of Pidgin in [URL="http://www.getdeb.net/release/4743"]http://www.getdeb.net
[/URL]

---

### Post by kranny on 2009-09-27
I Had the same problem once..Try to quit pidgin,

```
rm -rf .purple
```

and configure again your account.

---

### Post by finmanrushfan on 2009-10-05
thanks - removing .purple fixed it....why didnt the uninstall remove it?

---

