---
title: "E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by..."
date: 2008-09-06
forum: General Help
---

### Post by screwy on 2008-09-06
I have tried everything I could think of.  Everything in synaptic and aptitude.  I've tried updating my repositories, manually installing the packages...  I checked every relevant page on Google and most of them were questions of forums that went unanswered or talk of reinstalling...  I'm on Edgy (I know, I know, I'm behind) running KDE (though gnome is still installed...  Anyway, with the Edgy repositories, I get a 404 with spt-get -f install.  When I updated my repositories, I got this:

```
music@work:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libdbus-1-3: Depends: libc6 (>= 2.7-1) but 2.4-1ubuntu12.3 is installed
  libdbus-1-dev: Depends: libdbus-1-3 (= 0.93-0ubuntu3.1) but 1.2.1-3 is installed
  libgnomevfs2-0: Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed
                  Depends: libgnomevfs2-common (>= 1:2.14) but 2.16.1-0ubuntu7 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I have no idea what to do...  Can anyone help me?

---

### Post by zvacet on 2008-09-06
Edgy is not supported anymore and that is the reason why you can not update.Download Hardy and install it.

---

### Post by screwy on 2008-09-06
But I can't update it.  When I go to the update manager, I get this error message too.  It says I have broken packages.  How can I update without fixing the packages?

---

### Post by super_awesome on 2008-09-07
Instead of opening a new thread, and since my case is very similar, i figured i'd ask in here... I have ubuntu 6.06 installed because it was the only ubuntu cd I had. So I'm trying to update to 8.04 and am getting the same error. Here's the terminal output. Any suggestions would be appreciated. I'm still noobish to linux distributions so please be easy.

tristan@BTTOP:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  xbase-clients: Depends: x11-apps but it is not installed
                 Depends: x11-session-utils but it is not installed
                 Depends: x11-utils but it is not installed
                 Depends: x11-xfs-utils but it is not installed
                 Depends: x11-xkb-utils but it is not installed
                 Depends: x11-xserver-utils but it is not installed
  xkeyboard-config: Depends: xkb-data (>= 1.1~cvs.20080104.1-1ubuntu6) but it is not installed
  xserver-xorg-input-kbd: Depends: xserver-xorg-core (>= 2:1.4) but 1:1.0.2-0ubuntu10.13 is installed
  xserver-xorg-input-mouse: Depends: xserver-xorg-core (>= 2:1.4) but 1:1.0.2-0ubuntu10.13 is installed
  xserver-xorg-input-vmmouse: Depends: xserver-xorg-core (>= 2:1.4) but 1:1.0.2-0ubuntu10.13 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I also tried using synaptic, but failed as well.
Thanks in advance.

---

### Post by super_awesome on 2008-09-08
Edit: I finnaly found a copy of Hardy with a correct checksum, one that would actually install w/o crashing. Screw 6.06!

---

### Post by screwy on 2008-09-09
So is there any solution that does not require a complete reinstall?

---

### Post by screwy on 2008-09-10
So someone suggested that I just get rid of Gnome and KDE so I can do a clean dist-upgrade but now I'm getting this:

```
music@work:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.4-1ubuntu12.3) but 2.5-0ubuntu14 is installed
  libdbus-1-3: Depends: libc6 (>= 2.7-1) but 2.5-0ubuntu14 is installed
  libdbus-1-dev: Depends: libdbus-1-3 (= 0.93-0ubuntu3.1) but 1.2.1-3 is installed
E: Unmet dependencies. Try using -f.

```

So now libc6-i686 is broken and as far as I understand, it's pretty crucial.  Is there any way to fix this or am I really doomed to a complete reinstall?

---

