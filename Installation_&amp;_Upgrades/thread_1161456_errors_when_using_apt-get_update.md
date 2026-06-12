---
title: "errors when using apt-get update"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by kiwi-pete on 2009-05-16
Can someone please advise me on the cure or solution for the following errors I am experiencing on my system when I use apt-get update?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures were invalid: BADSIG 60D11217247D1CFF Launchpad PPA for OpenOffice.org Scribblers
W: Failed to fetch [http://deb.mulx.net/dists/jaunty/Release.gpg](http://deb.mulx.net/dists/jaunty/Release.gpg)  Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/jaunty/main/i18n/Translation-en_NZ.bz2](http://deb.mulx.net/dists/jaunty/main/i18n/Translation-en_NZ.bz2)  Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404 Not Found [IP: 204.9.165.83 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-amd64_Packages)

---

### Post by taurus on 2009-05-16
1.  You need to get the GPG key for ppa.launchpad.net, [https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA).

2.  You have a couple of dead repos in your /etc/apt/sources.list so you need to edit it and remove those two repos:  [http://deb.mulx.net/](http://deb.mulx.net/) & [http://download.skype.com/](http://download.skype.com/).

```
gksudo gedit /etc/apt/sources.list
```

3.  You have a duplicate repo for Medibuntu ([http://packages.medibuntu.org](http://packages.medibuntu.org)) so you need to remove the duplicate ones since you only need one entry for it.

Save all the changes and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by lildrumrgrl on 2009-05-20
I'm having a similar problem on Hardy.

W: Failed to fetch [http://deb.mulx.net/dists/hardy/Release.gpg](http://deb.mulx.net/dists/hardy/Release.gpg)  Could not resolve 'deb.mulx.net'

W: Failed to fetch [http://deb.mulx.net/dists/hardy/main/i18n/Translation-en_US.bz2](http://deb.mulx.net/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'deb.mulx.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

but there are no repos with that name in the source list.  I'm really new to ubuntu and am not entirely sure how to add or delete items from the source list.

---

### Post by Markor on 2009-05-22
You should change playonlinux repository, since it is on new location now, I think:

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)


First, remove that old source from sources.list,
by starting Software-sources applet or start Synaptic and go to
Settings->Repositories->Third-party-software, find it and click remove.
Then reload package list or just close and reload
or do an update to reload.
Then:

Ubuntu
Deb files :

With Jaunty repository
Type the following commands :
sudo wget [http://deb.playonlinux.com/playonlinux_jaunty.list](http://deb.playonlinux.com/playonlinux_jaunty.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

With Intrepid repository
Type the following commands :
sudo wget [http://deb.playonlinux.com/playonlinux_intrepid.list](http://deb.playonlinux.com/playonlinux_intrepid.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

With Hardy repository
Type the following commands :
sudo wget [http://deb.playonlinux.com/playonlinux_hardy.list](http://deb.playonlinux.com/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

---

### Post by lildrumrgrl on 2009-05-22
aaahhhh, thank you so much!! it worked.  it just feels so onimous with a yellow triangle and ! staring at you that something's wrong.

---

