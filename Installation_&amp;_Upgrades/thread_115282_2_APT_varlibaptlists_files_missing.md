---
title: "2 APT /var/lib/apt/lists files missing"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by rick333 on 2006-01-10
I started up Synaptic this morning and got the following error:

```

W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

An inspection of the directory indicates that these files are indeed missing. I'm concerned that my system is now somehow broken. Does anyone know what I should do about this?

**Here's the full list of files in the /var/lib/apt/lists directory:**

security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_breezy-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_breezy-security_Release
security.ubuntu.com_ubuntu_dists_breezy-security_Release.gpg
security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_breezy-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_breezy-security_universe_source_Sources
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release.gpg
Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_Release
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy_Release
us.archive.ubuntu.com_ubuntu_dists_breezy_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_breezy_universe_source_Sources

**Here's my /etc/apt/sources.list:**

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by rick333 on 2006-01-10
I think I figured out what the problem was. I think perhaps I updated sources.list outside of Synaptic and then when Synaptic is started, the above error shows up. Synaptic then dutifully creates the aforementioned files in /var/lib/apt/lists. So I don't think there is a problem.

However, here's a question for the gurus:

If the apt database gets corrupted, is there any way to regenerate it, or is a system re-install required to recover things?

Thanks... Rick

---

