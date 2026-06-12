---
title: "Repositories Not Authenticated?"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by LeeU on 2009-05-22
In the past few weeks, I have been getting a "Repositories Not Authenticated" error message when I tried to installed different software (e.g., Epiphany browser). When I reloaded the repositories, I get the following errors:

```

http://apt.wxwidgets.org/dists/gutsy-wx/main/binary-i386/Packages.bz2: Hash Sum mismatch
http://apt.wxwidgets.org/dists/gutsy-wx/main/source/Sources.bz2: Hash Sum mismatch
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]
http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz: 404 Not Found [IP: 91.189.88.46 80]

```

I am using Gutsy 7.10. Anybody have any ideas what is wrong?

---

### Post by yaroto98 on 2009-05-22
I'm not sure Gutsy is still supported. Hardy is the stable version that'll be supported for a while, and the current version Jaunty. Other than those, and I wouldn't be surprised if the repos give funky errors.  I'd suggest upgrading to at least Hardy.

---

### Post by TheNosh on 2009-05-22
gutsy is not supported anymore, so the repositories are no longer being hosted where they were. i think theres someplace that they've been moved to, but i would suggest upgrading to jaunty 9.04 or at least the latest LTS, hardy 8.04

---

### Post by taurus on 2009-05-22
Gutsy has been moved to here, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/).  Therefore, you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and replace the **[http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)** with **[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)** for all the repos.

Then save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by LeeU on 2009-05-22
Thanks, taurus! I'll check it out.

Okay, I don't have that exact line. What I have is this:

```

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu gutsy universe
# deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./
deb-src http://hydr0g3n.free.fr/qbittorrent/gutsy/ ./

# wxWidgets/wxPython repository at apt.wxwidgets.org
deb http://apt.wxwidgets.org/ gutsy-wx main
deb-src http://apt.wxwidgets.org/ gutsy-wx main

deb http://ppa.launchpad.net/tasque-packagers/ubuntu gutsy main

```

Which one do I need to change?

---

### Post by taurus on 2009-05-22
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by LeeU on 2009-05-22
Yeah, that's the one I want to use. I just need to back up 50 GB first.

BTW, see edited comment above ...

---

### Post by taurus on 2009-05-22
> 
**[COLOR="Blue"]#[/COLOR]**deb [http://hydr0g3n.free.fr/qbittorrent/gutsy/](http://hydr0g3n.free.fr/qbittorrent/gutsy/) ./
**[COLOR="Blue"]#[/COLOR]**deb-src [http://hydr0g3n.free.fr/qbittorrent/gutsy/](http://hydr0g3n.free.fr/qbittorrent/gutsy/) ./

# wxWidgets/wxPython repository at apt.wxwidgets.org
**[COLOR="Blue"]#[/COLOR]**deb [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main
**[COLOR="Blue"]#[/COLOR]**deb-src [http://apt.wxwidgets.org/](http://apt.wxwidgets.org/) gutsy-wx main

**[COLOR="Blue"]#[/COLOR]**deb [http://ppa.launchpad.net/tasque-packagers/ubuntu](http://ppa.launchpad.net/tasque-packagers/ubuntu) gutsy main

Put a # in front of those repos at the end to comment them out.  They are 3rd party repos and you don't need them anymore.

Then replace everything else from [http://archive.ubuntu.com/](http://archive.ubuntu.com/) to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) so it would look something like this.

```

deb http://old-releases.ubuntu.com/gutsy main restricted universe multiverse

```

---

### Post by LeeU on 2009-05-22
That worked great! Thanks!

Just curious, why **gk**sudo instead of just sudo?

---

### Post by Shrekster on 2010-06-22
gksudo or gksu is used for graphical apps.
Though, one should not use the `terminal` sudo for such apps as it might cause problems with the expansion of the root $HOME or "~" in their code, it works most of the time where applications do not make extensive use of the enviornment variables. For example, sudo uses the current user's home dir (for eg, /home/currentuserhome) while gksu/gksudo sets the environment variable to /home/root. Now, this might not follow under some circumstances, there are still lot many reasons to not use the improper way of running a graphical app from terminal.

---

