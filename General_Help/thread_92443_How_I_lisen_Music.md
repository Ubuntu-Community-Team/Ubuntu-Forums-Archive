---
title: "How I lisen Music?"
date: 2005-11-19
forum: General Help
---

### Post by annie on 2005-11-19
Hello My name is Annie. I need help with my Synaptic Package Manager it dos not work rightly. I Get this Error when I open:

W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/universe/ndeb Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_universe_ndeb_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/http://uk.archive.ubuntu.com/ubuntu Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_http:__uk.archive.ubuntu.com_ubuntu_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/breezy Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_breezy_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I live in US but my fiend said to change URLS to uk one.  Also cannot search for thing. Plese Help!

{Sorry My English is not so Good I learning :smile: }

---

### Post by Bachstelze on 2005-11-19
just click on the "Reload" button in Synaptic :)

---

### Post by annie on 2005-11-19
I click Reload:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

In A box:
[http://uk.archive.ubuntu.com/ubuntu/dists/breezy/Release:](http://uk.archive.ubuntu.com/ubuntu/dists/breezy/Release:) Unable to find expected entry  universe/ndeb/binary-i386/Packages in Meta-index file (malformed Release file?)

:confused:

---

### Post by Bachstelze on 2005-11-19
Your sources.list must be f***ed up. Close Synaptic, run

```
$ sudo gedit /etc/apt/sources.list
```

Then delete everything and replace with this

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

Then you can reopen Synaptic and click Reload or run

```
$ sudo apt-get update
```

---

### Post by annie on 2005-11-19
Oh My it works!

thank you!

---

### Post by Bachstelze on 2005-11-19
You're welcome :)

---

### Post by mztriz on 2005-11-19
[QUOTE=annie]Oh My it works!

thank you![/QUOTE]

i lover you.

---

