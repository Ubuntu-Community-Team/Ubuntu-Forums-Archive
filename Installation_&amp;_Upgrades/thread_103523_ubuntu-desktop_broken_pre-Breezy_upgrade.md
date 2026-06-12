---
title: "ubuntu-desktop broken pre-Breezy upgrade"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by keyshawn on 2005-12-14
Hi,

I'm trying to upgrade from hoary to breezy [late, yes, I was away at college and I'm upgrading the home computer right now]. So, I found the 
[Wiki's BreezyUpgradeNotes]("https://wiki.ubuntu.com/BreezyUpgradeNotes")and I tried to install the ubuntu-desktop and base packages [because they were not] and I received this error message.

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: bluez-pcmcia-support but it is not going to be installed
                  Depends: bluez-pin but it is not going to be installed
                  Depends: bluez-utils but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: evolution-plugins but it is not going to be installed                  Depends: firefox-gnome-support but it is not going to be installed
                  Depends: gdm but it is not going to be installed
                  Depends: gnome-app-install but it is not going to be installed                  Depends: gnome-netstatus-applet but it is not going to be installed
                  Depends: gnome-pilot-conduits but it is not going to be installed
                  Depends: gnome-system-monitor but it is not going to be installed
                  Depends: gnome-system-tools but it is not going to be installed
                  Depends: hwdb-client but it is not going to be installed
                  Depends: libgl1-mesa but it is not going to be installed
                  Depends: libpt-plugins-v4l but it is not going to be installed                  Depends: notification-daemon but it is not going to be installed
                  Depends: openoffice.org2-gnome but it is not going to be installed
                  Depends: update-notifier but it is not going to be installed
                  Depends: x-window-system-core but it is not going to be installed
                  Depends: xkeyboard-config but it is not going to be installed
                  Depends: yelp but it is not going to be installed
E: Broken packages

```


I think it's because I already edited my sources.list to be breezy, and I may have to revert them back to hoary to download those pkg's described above. I am hesitant to do this for fear of borking my system. And, for reference, I did remove the mozilla packages successfully.

regards,
keyshawn

---

### Post by aysiu on 2005-12-14
I'm confused. You're trying to install ubuntu-desktop... you didn't have that installed already?

Also in what order did you do things? I'm assuming you changed your sources.list to Breezy *before* doing the ```
sudo apt-get dist-upgrade
``` Is that correct?

Can I take a gander at your sources.list, by the way?

---

### Post by keyshawn on 2005-12-16
I ended up fixing it myself, by switching my sources list back to Hoary and then downloaded the ubuntu-desktop and base metapackages that I needed. 
After that, I changed my sources list to breezy and then successfully did the 
dist-upgrade.

*Now, to figure out why X is giving me problems.*

regards,
will.

---

