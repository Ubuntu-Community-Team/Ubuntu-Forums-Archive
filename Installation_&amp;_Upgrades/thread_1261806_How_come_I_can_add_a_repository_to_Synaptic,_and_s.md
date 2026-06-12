---
title: "How come I can add a repository to Synaptic, and still not see it's contents?"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by hoppipolla on 2009-09-09
Just now I added the Kubuntu PPA and searched for Amarok.. and it wasn't there :(

Does it just take a while for it to come up? I did click Reload ._.

Hoppi

---

### Post by wojox on 2009-09-09
Don't know? I didn't add Kubuntu PPA and I searched Amarok and it came right up. Jaunty/Gnome is what I use.

---

### Post by alienclone on 2009-09-09
are you sure you have "ALL" selected on the left?

---

### Post by hoppipolla on 2009-09-09
> **wojox said:**
> Don't know? I didn't add Kubuntu PPA and I searched Amarok and it came right up. Jaunty/Gnome is what I use.

Amarok comes up but it's the old one - 2:2.0.2mysql5.1.30 ...

And yeah all is selected, and I use Jaunty, Gnome and Synaptic ._.

Weird man ._.

Wakoopa didn't appear for a while either but I think it appeared after a short time when I restarted Synaptic or something..

---

### Post by mc4man on 2009-09-09
try running this 
```
sudo update-apt-xapian-index
```

maybe related to this
[http://ubuntuforums.org/showthread.php?t=1211277](http://ubuntuforums.org/showthread.php?t=1211277)

---

### Post by hoppipolla on 2009-09-09
New Amarok still isn't there I don't think... I dunno maybe I am doing something wrong...

---

### Post by mc4man on 2009-09-09
I don't use jaunty nor kubuntu but I believe if you where to add backports to your sources you'd get the newer amarok

System -> Admin... -> Software Sources -> Updates and tick the backports box    (I wouldn't enable proposed

---

### Post by hoppipolla on 2009-09-09
> **mc4man said:**
> I don't use jaunty nor kubuntu but I believe if you where to add backports to your sources you'd get the newer amarok

System -> Admin... -> Software Sources -> Updates and tick the backports box    (I wouldn't enable proposed

Beautiful, well done :)

To be honest, I always thought that option was only for like... updates as defined in the Update Manager etc, as opposed to software listings in Synaptic.

It does however make sense to include them in there, seeing as they are upgrades of software and not separate programs!

Thanks again, well spotted :)

---

### Post by mc4man on 2009-09-09
If you tend to do 'blanket' updates from the update manager then I'd probably not leave backports enabled, if you look thru updates before applying then it would be ok to leave.

You may get an update you don't wish otherwise

Just to note
The proposed are updates that are as yet to be confirmed as stable, more like a testing thing, I'd be very careful with those and never leave enabled.

---

### Post by hoppipolla on 2009-09-09
> **mc4man said:**
> If you tend to do 'blanket' updates from the update manager then I'd probably not leave backports enabled, if you look thru updates before applying then it would be ok to leave.

You may get an update you don't wish otherwise

Just to note
The proposed are updates that are as yet to be confirmed as stable, more like a testing thing, I'd be very careful with those and never leave enabled.

Oo crap, I used to leave them enabled all the time!! (ages ago when I used to use Ubuntu at around 7.04!)

Lesson noted!

Actually though, I don't think enabling unsupported did fix it :( It just gave me a slightly newer version of 2.1. Damn :(

Am I just supposed to install from here:

[https://edge.launchpad.net/~kubuntu-ppa/+archive/beta](https://edge.launchpad.net/~kubuntu-ppa/+archive/beta)

I tried that too but just got "dependency hell" lol :)

---

### Post by mc4man on 2009-09-09
The one on that ppa is slightly newer ( though not necessarily better)

 The best way to get is to add that ppa to your sources ( same place where you enable backports, except under the 3rd party tab.

( is this the ppa you added before..?

If you tried to add from that ppa directly the order would be amarok -common, amarok-utils, then amarok

I don't think you should have any issues with amarok's depends ater common and utils are installed ( or if you add the ppa to your sources


Here's the list for that version of amarok (simile is 8

> Maintainer: Kubuntu Developers <kubuntu-devel@ubuntu.com>
Installed-Size: 131104
Depends: amarok-common (= 2:2.1.80-0ubuntu2~ppa1), amarok-utils (= 2:2.1.80-0ubuntu2~ppa1), phonon-backend-xine | phonon-backend, kdebase-runtime (>= 4:4.3.0), kdelibs5 (>= 4:4.3.1), libc6 (>= 2.8), libcurl3-gnutls (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libgcrypt11 (>= 1.4.2), libglib2.0-0 (>= 2.14.0), libgpod4 (>= 0.7.0), libgtk2.0-0 (>= 2.17.10), liblastfm0, libloudmouth1-0 (>= 1.1.4-2), libmtp8 (>= 0.3.1), libmysqlclient16 (>= 5.1.21-1), libplasma3 (>= 4:4.3.1-0ubuntu1), libqt4-dbus (>= 4.5.1), libqt4-network (>= 4.5.1), libqt4-phonon (>= 4.5.1), libqt4-script (>= 4.5.1), libqt4-sql (>= 4.5.1), libqt4-svg (>= 4.5.1), libqt4-webkit (>= 4.5.1), libqt4-xml (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libstdc++6 (>= 4.4.0), libstreamanalyzer0 (>= 0.7.0), libstreams0 (>= 0.7.0), libtag-extras0 (>= 0.1.1), libtag1c2a (>= 1.5), libxml2 (>= 2.6.27), zlib1g (>= 1:1.1.4), libqtscript4-core, libqtscript4-gui, libqtscript4-network, libqtscript4-xml, libqtscript4-sql, libqtscript4-uitools
> Recommends: kdemultimedia-kio-plugins (>= 4:4.2.0)
> Suggests: libqt4-sql-sqlite, libqt4-sql-mysql, libqt4-sql-psql
> Conflicts: amarok-engine-xine (<< 2), amarok-engine-yauap (<< 2), amarok-kde4
Replaces: amarok-common (<< 2:2.1.1orig-0ubuntu2), amarok-kde4



Any issues post this
```
cat /etc/apt/sources.list
```

---

### Post by hoppipolla on 2009-09-13
I still couldn't get amarok working, but yeah sometimes things just don't list ._.

I need to install them from the prompt by stating their name directly like:

sudo apt-get install chromium-browser


I hope this little glitch is fixed by Karmic :)


Sometimes they do pop up in Synaptic later on, that's what happened with Wakoopa before I installed it... strange though :)

---

