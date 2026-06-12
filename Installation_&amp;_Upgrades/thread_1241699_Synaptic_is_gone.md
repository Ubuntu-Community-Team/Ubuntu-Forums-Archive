---
title: "Synaptic is gone"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by gaussfan on 2009-08-16
Hello all,

Just recently upgraded from 7.10 to 8.04, and wad getting everything updated.  Once I updated apt-xapian-index to 0.6, I lost synaptic.  The System->Administration menu no longer has Synaptic, the Update Manager, or Software Sources.

When I try to use apt-get, I'm told that synaptic requires at least apt-xapian-index 0.8, but trying to upgrade apt-xapian-index doesn't find anything newer than 0.6, so I seem to be stuck.

I've tried searching the forums quite a bit, and though some issues have come close, I didn't see anyone else with the same problem.

Can anyone help me get these back?  I appreciate any help!

---

### Post by Soul-Sing on 2009-08-16
: [https://launchpad.net/ubuntu/intrepid/sparc/apt-xapian-index/0.8](https://launchpad.net/ubuntu/intrepid/sparc/apt-xapian-index/0.8)
is it possible to install the 0.8 .deb?

---

### Post by Partyboi2 on 2009-08-16
Open a terminal and try
```
sudo apt-get --reinstall install ubuntu-desktop
```This should reinstall synaptic, update-manager , post any errors.

---

### Post by gaussfan on 2009-08-16
> **Partyboi2 said:**
> Open a terminal and try
```
sudo apt-get --reinstall install ubuntu-desktop
```This should reinstall synaptic, update-manager , post any errors.

Tried this first, here's what I got:

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: gnome-app-install but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: software-properties-gtk but it is not going to be installed
                  Depends: synaptic but it is not going to be installed
                  Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: ubufox but it is not going to be installed
E: Broken packages

---

### Post by gaussfan on 2009-08-16
> **leoquant said:**
> : [https://launchpad.net/ubuntu/intrepid/sparc/apt-xapian-index/0.8](https://launchpad.net/ubuntu/intrepid/sparc/apt-xapian-index/0.8)
is it possible to install the 0.8 .deb?

OK, my bad for thinking I could shorthand, apparently.  I was able to install this .deb, but now running 'sudo apt-get install synaptic' gives me this:

The following packages have unmet dependencies:
  synaptic: Depends: apt-xapian-index (>= 0.8ubuntu1~ppa1) but 0.8 is to be installed
E: Broken packages


So it's not 0.8, but 0.8ubuntu1~ppa1 that I need.  Sorry for assuming . . .

---

### Post by Partyboi2 on 2009-08-16
Can you post your sources.list please
```
cat /etc/apt/sources.list
```

---

### Post by gaussfan on 2009-08-16
> **Partyboi2 said:**
> Can you post your sources.list please
```
cat /etc/apt/sources.list
```

Away from home right now, I'll post as soon as I'm back this afternoon.

---

### Post by Partyboi2 on 2009-08-16
> Away from home right now, I'll post as soon as I'm back this afternoon. 	
I am going to bed soon, so  if you know how to disable repos in your sources.list try disabling all your ppa repos and then try reinstall synaptic. If you are not sure how to make the changes someone should be able to help.

---

### Post by gaussfan on 2009-08-16
> **Partyboi2 said:**
> Can you post your sources.list please
```
cat /etc/apt/sources.list
```

OK, first I'll get this posted.  I've commented out the ppa repos to disable them as suggested.  It didn't allow me to reinstall ubuntu-desktop (I'll put that info in the next post), but it did allow me to install synaptic (victory #1!).

Here's the file - I'm happy to take suggestions if I should disable anything else:
# Repository List based on standard hardy with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
#  gpg --keyserver subkeys.pgp.net --recv KEY
#  gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
#  wget URL --quiet -O - | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
#  sudo apt-key add FILE
#
# In the repository list page there's also a script that can do this
# work automatically, this is suggested only if you know what you're doing

# Ubuntu supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed main restricted

# Ubuntu community supported packages (GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-proposed universe multiverse

# Ubuntu backports project (GPG key: 437D05B5)
deb [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) hardy-backports main restricted universe multiverse
deb-src [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) hardy-backports main restricted universe multiverse


# Bleeding edge wine packages (GPG key: 387EE263)
# GPG key-file: [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

# The Opera browser (packages) (GPG key: 6A423791)
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free

# Google picasa packages (GPG key: 7FAC5991)
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


# Skype packages
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# Geole's Ubuntu Repository
## to get the key - in terminal type: sudo aptitude install geole-keyring
deb [http://debian.geole.info/](http://debian.geole.info/) etch main contrib non-free
deb-src [http://debian.geole.info/](http://debian.geole.info/) etch main contrib non-free
deb [http://debian.geole.info/](http://debian.geole.info/) etch-backports main contrib non-free
deb-src [http://debian.geole.info/](http://debian.geole.info/) etch-backports main contrib non-free

# Asher256's Repository
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu french

# gnomemeeting - ekiga (GPG key: 52ABFCB1)
deb [http://snapshots.ekiga.net/snapshots/ubuntu/](http://snapshots.ekiga.net/snapshots/ubuntu/) hardy main



## lprod packages: many audio/video apps: avidemux, cinelerra...
deb [http://lprod.org/deb/hardy/](http://lprod.org/deb/hardy/) ./
deb-src [http://lprod.org/deb/hardy/](http://lprod.org/deb/hardy/) ./

# Morgoth Repository (GPG key: 7E2E4741)
# Provides Monkey's Audio, xmms pugins, vlc plugins, gqview, audacius, audacity...
# GPG key-file: [http://morgoth.free.fr/files/morgoth-signkey.gpg.asc](http://morgoth.free.fr/files/morgoth-signkey.gpg.asc)
deb [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) hardy-backports main
deb-src [http://morgoth.free.fr/ubuntu](http://morgoth.free.fr/ubuntu) hardy-backports main


# edevelop - e17 (Enlightenment DR 17)
# GPG key: [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)
deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) hardy e17
deb-src [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) hardy e17


# The Ubuntu NLP Repository (GPG key: 8ABD1965)
# GPG key-file: [http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg](http://cl.naist.jp/~eric-n/ubuntu-nlp/8ABD1965.gpg)
deb [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) hardy all
deb-src [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) hardy all



# Le d&#65533;pomaniak repository (GPG key: 1D59E694)
# GPG key-file: [http://ubuntu.davromaniak.eu/1D59E694.gpg](http://ubuntu.davromaniak.eu/1D59E694.gpg)
deb [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) hardy-depomaniak all
deb-src [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) hardy-depomaniak all


# Trevi&#65533;o's Ubuntu hardy Fawn Repository (GPG key: 81836EBF - DD800CD9)
# Many "random" bleeding edge software: aMule, aMSN, Mercury, flash...
# Further informations and complete packages list: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty 3v1n0

## Trevi&#65533;o's Ubuntu Suspend2 patched kernels Repository (GPG key: 81836EBF - DD800CD9)
## Ubuntu kernels patched with Suspend2 plus other related tools [www.suspend2.net](www.suspend2.net)
## Warning: they will replace standard ubuntu kernel related packages
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty suspend2
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) feisty/

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
# deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy main universe
# deb [http://ppa.launchpad.net/mvo/ubuntu](http://ppa.launchpad.net/mvo/ubuntu) hardy main
## key AF425CB5
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) hardy-cafuego google inkscape internode rtorrent secondlife
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) hardy-cafuego google inkscape internode rtorrent secondlife
deb [http://e17.dunnewind.net/ubuntu](http://e17.dunnewind.net/ubuntu) gutsy e17
deb [http://download.tuxfamily.org/geubuntu/](http://download.tuxfamily.org/geubuntu/) gutsy/



# deb [http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/](http://download.tuxfamily.org/shames/debian-sid/desktopfx/unstable/) ./
# deb [http://ppa.launchpad.net/superm1/ubuntu](http://ppa.launchpad.net/superm1/ubuntu) hardy main
# deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main

---

### Post by gaussfan on 2009-08-16
> **Partyboi2 said:**
> I am going to bed soon, so  if you know how to disable repos in your sources.list try disabling all your ppa repos and then try reinstall synaptic. If you are not sure how to make the changes someone should be able to help.

After disabling as shown in the previous post, here is the response to trying to reinstall ubuntu-desktop:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Broken packages

---------------

When I try to install update-manager, I get:

The following packages have unmet dependencies:
  update-manager: Depends: update-manager-core (= 1:0.87.31) but 1:0.91.6 is to be installed
E: Broken packages
----------------

Which seems to say the version of update-manager-core is too new?  Is this a case of another repo I need to disable?

Thanks again for all the help.

---

### Post by gaussfan on 2009-08-16
OK seems I'm back in business now.  Using Synaptic, I forced update-manager-core to revert to the older version that update-manager said it needed, and was able to install it.  Then the reinstall of ubuntu-desktop worked without a hitch.

I'd still love to get someone's feedback on the sources I have in my sources.list file post above, to see if there are any other repos I should disable to avoid getting components out of sync like that.

Thanks again for all your help!
Mike


> **gaussfan said:**
> After disabling as shown in the previous post, here is the response to trying to reinstall ubuntu-desktop:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: update-manager but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
E: Broken packages

---------------

When I try to install update-manager, I get:

The following packages have unmet dependencies:
  update-manager: Depends: update-manager-core (= 1:0.87.31) but 1:0.91.6 is to be installed
E: Broken packages
----------------

Which seems to say the version of update-manager-core is too new?  Is this a case of another repo I need to disable?

Thanks again for all the help.

---

### Post by Partyboi2 on 2009-08-16
Hardy-proposed repos could have caused the 'update-manager-core' problem.

---

### Post by gaussfan on 2009-08-17
> **Partyboi2 said:**
> Hardy-proposed repos could have caused the 'update-manager-core' problem.

OK - I'll comment them out, too.

---

