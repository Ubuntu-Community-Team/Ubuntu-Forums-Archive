---
title: "Can't find 'pine' package in Jaunty"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by noahp on 2009-08-05
Let me apologize in advance if I've [likely] misunderstood something about how apt works, but here's what I'm seeing:

1) Using Jaunty (9.04) 64 bit
2) In /etc/apt/sources.list, among other lines I have:

```
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
```

3) I ran 'sudo apt-get update' and it completes successfully.
4) I try to install pine using: 'sudo apt-get install pine' and then I get this message:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package pine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pine has no installation candidate
```

I think 'pine' should be there, though, no?  I am looking at [http://packages.ubuntu.com/source/jaunty/pine](http://packages.ubuntu.com/source/jaunty/pine) and it's there.  But then (and here's where I may be misunderstanding), looking at the index here [http://us.archive.ubuntu.com/ubuntu/indices/override.jaunty.multiverse](http://us.archive.ubuntu.com/ubuntu/indices/override.jaunty.multiverse) it looks like 'pine' is not listed.

So two questions:  why can't apt find the pine package?  and how can I install it?

I'll post my full sources.list below.  Thanks a lot for any help!

Also -- if I run 'apt-cache search pine' here is the output:

```
$ apt-cache search pine
fetchmail - SSL enabled POP3, APOP, IMAP mail gatherer/forwarder
lbdb - The little brother's database for the mutt mail reader
libgpg-error-dev - library for common error values and messages in GnuPG components
libgpg-error0 - library for common error values and messages in GnuPG components
mutt - text-based mailreader supporting MIME, GPG, PGP and threading
nano - free curses-based text editor, inspired by Pico
pinentry-doc - documentation for pinentry packages
pinentry-gtk2 - GTK+-2-based PIN or pass-phrase entry dialog for GnuPG
pinentry-qt - Qt-based PIN or pass-phrase entry dialog for GnuPG
pinentry-qt4 - Qt-4-based PIN or pass-phrase entry dialog for GnuPG
2vcard - perl script to convert an addressbook to VCARD file format
alpine - Text-based email client, friendly for novices but powerful
alpine-dbg - Text-based email client's debugging symbols
alpine-pico - Simple text editor from Alpine, a text-based email client
cacti-cactid - Multi-Threading poller for cacti (transitional package)
cacti-spine - Multi-Threading poller for cacti
libmail-cclient-perl - Interface to UW c-client library
mew-beta-bin - external commands for Mew (development version)
mew-bin - external commands for Mew
nano-tiny - free curses-based text editor, inspired by Pico - tiny build
netrik - text mode WWW browser with vi like keybindings
pilot - Simple file browser from Alpine, a text-based email client
pinentry-curses - curses-based PIN or pass-phrase entry dialog for GnuPG
sanitizer - The Anomy Mail Sanitizer - an email virus scanner
topal - Links Pine and GnuPG together
opendict-plugins-lingvosoft - plugins for OpenDict - LingvoSoft Online Dictionaries
pgp4pine - A PGP/GPG Wrapper for Pine
```


Full sources.list:
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

#
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
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
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse


### from https://help.ubuntu.com/community/FreeNX
deb http://ppa.launchpad.net/freenx-team/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/freenx-team/ppa/ubuntu jaunty main

```

---

### Post by noahp on 2009-08-05
Okay, I've learned a little more and will post the results below in case it helps anyone.  

However: if there is a better way to accomplish running Pine on Ubuntu Jaunty 64 bit, I'd very much welcome suggestions.

So it looks like there are not binaries distributed for pine.  You can either find a .deb file (see [http://ubuntuforums.org/showthread.php?t=362724](http://ubuntuforums.org/showthread.php?t=362724)), or build it from source.  Since that .deb is for i386 and I need amd64, I went with the source route.  This post was helpful [http://ubuntuforums.org/showthread.php?t=256220](http://ubuntuforums.org/showthread.php?t=256220) 

This is (I think) the sequence that worked for me.  It's possible some of those packages are not needed:

```
  $ apt-get install pine-src
  $ sudo apt-get install libssl-dev libpam0g-dev libssl0.9.8 lib32ncurses5-dev libldap2-dev
  $ cd pine-4.64
  $ ./build SSLDIR=/etc/ssl SSLINCLUDE=/usr/include/openssl SSLLIB=/usr/lib/ssl lnp
  $ ./bin/pine -version
  Pine 4.64 built Wed Aug 5 16:18:56 EDT 2009 on locohost
```

So now just copy the contents of ./bin to /usr/local/bin or similar and you're ready to run pine.

---

### Post by slakkie on 2009-08-05
Look for alpine, pine is no longer being developed, alpine is a fork. I use it at work.

See [http://www.washington.edu/alpine/overview/story.html](http://www.washington.edu/alpine/overview/story.html)

---

### Post by noahp on 2009-08-05
Slakkie, thank you!  Anyone else finding this post through a search, please disregard the convoluted instructions above -- you need only to install alpine as Slakkie suggests.  Great!

```
sudo apt-get install alpine
```

Then run alpine!  Thanks again -- this forum is excellent.

---

