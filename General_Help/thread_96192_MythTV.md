---
title: "MythTV"
date: 2005-11-28
forum: General Help
---

### Post by blaha on 2005-11-28
How do I install it? I cant find it among the apt packages. And I need it, because Tvtime won't work with my px-tv402u converter.

---

### Post by munkiller on 2005-11-28
[QUOTE=blaha]How do I install it? I cant find it among the apt packages. And I need it, because Tvtime won't work with my px-tv402u converter.[/QUOTE]


Last time i tryed this got it all working but the feature i wanted the TV-guide did not work 100% (as im based in SA).. had to hak my way around but the best place for info is on the MyTV forums.. (Note i had a helping hand, and it still took me a month from the start to the first day i booted into mytv). Must say the exprience i had with 5.05 was not the best in the world.. would recomend using Gentoo or some thing more suited to MyTV. 

Sorry but Ubuntu not too friendly with MyTV.. will require alot of forum searching and some luck ;) . 

PS: im still newbie (but had fairly good user aid me) only been using the windows bashing bird for 2.5-3 years.

---

### Post by djselbeck on 2005-11-28
I think Ubuntu is good for MythTV. I have the actually SVN Version running and it seems to become better every SVN update i do. It was very easy to install. You only must download the source code or the binary packages from the Repository and install them. If you had done this you must make sure that an Mysql server is running on you system. if this is done you import the Database of mythtv. if you downloaded the source it is in the database directory (mc.sql). now you must make sure that mythbackend is running. it is best if you let it start during boot and only start mythfrontend if you need it. But before this you must run mythtv-setup on time because it search for TV-Channels and ask you some settings.

DJSelbeck. 

PS: I don't lile if someone say that Ubuntu is not a good distribution for mythtv because every distribituion is good enough for mythtv you only need some libaries and the box starts running and running and running. ;)

---

### Post by frodon on 2005-11-28
There is an HOWTO about that : [http://www.ubuntuforums.org/showthread.php?t=91511](http://www.ubuntuforums.org/showthread.php?t=91511)

---

### Post by blaha on 2005-11-28
> You only must download the source code or the binary packages from the Repository and install them.
From what repository? I can't find ANYTHING called mythtv in ANY repository. I have added all available sources in synaptic.

> There is an HOWTO about that : [http://www.ubuntuforums.org/showthread.php?t=91511](http://www.ubuntuforums.org/showthread.php?t=91511)
I've already tried that howto and it diddn't work.

---

### Post by jonny on 2005-11-28
Myth is installed and working perfectly for me on Breezy with a Hauppage Nova-T DVB card in the UK.  It's a great way of making your mates wish they knew more about linux - the consensus seems to be that it kicks dust in the face of the commercial alternatives.

I can't remember which repositories I got things from, but here's my /etc/apt/sources.list.
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

```A couple of pointers for you:
 - I had to find and run the database setup script by hand.  As a result, Synaptic tells me that mythtv isn't properly set up.
 - Tuning the card and setting up the channels took a huge amount of googling and some manual editing of the mysql tables.  If you have to do the same, make sure you install a decent gui tool for mysql, like the mysql query browser.
 - MythGame won't install for me (unresolvable dependencies) but I really don't care.
 - I needed to get a new .deb off the web for mythdvd, as the ubuntu package won't rip dvds - something to do with patents, I guess
 - To get the best out of Myth, you'll need to install mplayer and a good set of codecs.  Plenty of advice can be found on both topics in the forums - unfortunately, legal issues prevent mplayer being freely distributed.
 - When myth is first installed, you'll need to log in as mythtv (installing the packages creates a new user with this name) and run mythtv-setup.  After that's done, you can run myth-frontend as a normal user
 - The myth site has extensive documentation, but nothing specific to ubuntu.   It also assumes that you're compiling from source, so it can be rather confusing at times.

---

### Post by RAOF on 2005-11-28
It's in the repositories:
```
chris@RAOF:~$ apt-cache show mythtv
Package: mythtv
Priority: optional
Section: multiverse/graphics
Installed-Size: 64
Maintainer: Matt Zimmerman <mdz@debian.org>
Architecture: all
Version: 0.18.1-5
Depends: mythtv-database (= 0.18.1-5), mythtv-frontend (= 0.18.1-5), mythtv-backend (= 0.18.1-5)
Recommends: mythtv-doc, mythtv-themes
Filename: pool/multiverse/m/mythtv/mythtv_0.18.1-5_all.deb
Size: 17220
MD5sum: 2a7d74e4675c344af86ec7e93acc2529
Description: A personal video recorder application (client and server)
 MythTV implements the following PVR features, and more, with a
 unified graphical interface:
 .
  - Basic 'live-tv' functionality. Pause/Fast Forward/Rewind "live" TV.
  - Video compression using RTjpeg or MPEG-4
  - Program listing retrieval using XMLTV
  - Themable, semi-transparent on-screen display
  - Electronic program guide
  - Scheduled recording of TV programs
  - Resolution of conflicts between scheduled recordings
  - Basic video editing
 .
 http://www.mythtv.org/
 .
 This package will install a complete MythTV client/server environment
 on a single system.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```As you may be able to see from that, it's in the universe repository.
If you've enabled that, you'll be able to install mythtv.  (Unless you want to install it on a 64bit breezy system.  Last time I checked, the 64bit packages had dependency problems).

---

### Post by LodeRunner on 2005-12-06
I had the same problem.  Add:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy multiverse

to your sources.list.  It gives an error, but Synaptic was able to find mythtvpackages.

---

