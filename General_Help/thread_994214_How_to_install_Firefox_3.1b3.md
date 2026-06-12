---
title: "How to install Firefox 3.1b3"
date: 2008-11-26
forum: General Help
---

### Post by timchesonis on 2008-11-26
Does anyone know how to install Firefox 3.1 beta 3 that just came out?  One can find the file on Mozilla's site at [http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/).

I'm running the i686 (32 bit version) of Ubuntu, and I have Firefox 3.1 beta 2 installed now.

---

### Post by ITC on 2008-12-08
Have a look at [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
and [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Good luck.

Edit: You can also have a look here [https://launchpad.net/~fta/+archive](https://launchpad.net/~fta/+archive)
and ad to your sources.list entries

---

### Post by Endolith on 2008-12-15
> **ITC said:**
> Have a look at [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)
and [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Good luck.

Edit: You can also have a look here [https://launchpad.net/~fta/+archive]("https://launchpad.net/%7Efta/+archive")
and ad to your sources.list entries

None of those tells how to install 3.1b3.  The PPA is at 3.1b2.  Are there instructions for 3.1b3?

---

### Post by frankleeee on 2008-12-15
There is a FF3.1 in synaptic in Intrepid, if you install it don't remove 3.04: 3.1 wont run without it installed. I guess b2 is in synaptic.

---

### Post by Endolith on 2008-12-15
> **frankleeee said:**
> There is a FF3.1 in synaptic in Intrepid, if you install it don't remove 3.04: 3.1 wont run without it installed. I guess b2 is in synaptic.

There is?  Are you sure you don't have another repository installed?

---

### Post by frankleeee on 2008-12-15
I have the backports and all the extras in sources on but here is my apt list if it helps. You are already running the same FF b2 as me b3 isn't in synaptic. I just noticed a hardy link I think that is from ubuntu tweak 3rd party.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) intrepid main
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main #Firefox
# deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main #OpenOffice.org
deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) intrepid main

# deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) intrepid main
# deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) intrepid main

---

### Post by adult swim on 2008-12-15
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main #Firefox
that is where you are getting your firefox 3.1 from

---

### Post by frankleeee on 2008-12-15
> **adult swim said:**
> deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) intrepid main #Firefox
that is where you are getting your firefox 3.1 from

I thought that was the case thanks, runs great and I have a link to a about:config hack to not block Mozilla add-ons in 3.1.
[http://www.jkontherun.com/2008/06/how-to-force-fi.html](http://www.jkontherun.com/2008/06/how-to-force-fi.html)

---

