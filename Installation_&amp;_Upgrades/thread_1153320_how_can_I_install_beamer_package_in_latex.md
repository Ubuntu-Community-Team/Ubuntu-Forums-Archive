---
title: "how can I install beamer package in latex"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by BecoSalih on 2009-05-08
Hi friends, 
I wanna install beamer package for latex presentation in Ubuntu. I tried the following command: sudo apt-get install beamer-latex
but I got the following error message:

Err [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) gutsy/main latex-xcolor 2.09-1
  404 Not Found [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2007-10_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/t/texlive-base/texlive-latex-recommended_2007-10_all.deb)  404 Not Found [IP: 130.239.18.137 80]
Failed to fetch [http://se.archive.ubuntu.com/ubuntu/pool/main/l/latex-xcolor/latex-xcolor_2.09-1_all.deb](http://se.archive.ubuntu.com/ubuntu/pool/main/l/latex-xcolor/latex-xcolor_2.09-1_all.deb)  404 Not Found [IP: 130.239.18.137 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

thanks in advance
Beco

---

### Post by taurus on 2009-05-08
Gutsy has reached the end of it life so the repos have been moved to old-releases.ubuntu.com.  Therefore, you need to edit /apt/sources.list and replace the se.archive.ubuntu.com with the old-releases.ubuntu.com.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by BecoSalih on 2009-05-08
Hi [taurus]("http://ubuntuforums.org/member.php?u=43398")
thanks for your reply, one more question how can I edit my apt/sources.list
I have used this command: sudo nano /etc/apt/sources.list
with ctrl+o to save, ctrl+x to exit.
I have change the links to the one you mentioned but I could not mange to exit successfully

---

### Post by taurus on 2009-05-08
To save and exit, hold down the <Ctrl> key while hitting the x key.  It will ask you if you want to save it.  Use the arrow key to answer yes.

---

### Post by BecoSalih on 2009-05-08
Here what I have in my apt/source list
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main re$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) gutsy main restricted
deb-src [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) gutsy-updates main restricted
deb-src [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) gutsy universe
deb-src [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/) gutsy universe
And here what I have when I tried to install beamer
> Package latex-beamer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package latex-beamer has no installation candidate

this after the changes of the links in apt/sources.list

---

### Post by BecoSalih on 2009-05-09
More ideas?

---

### Post by Partyboi2 on 2009-05-09
Hi, open your sources.list and comment out (#) your cdrom entry
```
gksu gedit /etc/apt/sources.list
``````
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main re$
``````
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main re$
```then save and close gedit and run
```
sudo apt-get update && sudo apt-get install latex-beamer
```

---

### Post by BecoSalih on 2009-05-09
still same result!!! 

Package latex-beamer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package latex-beamer has no installation candidate

---

### Post by Stefan_K on 2009-05-10
Hi BecoSalih,

perhaps consider to install [TeX Live 2008]("http://tug.org/texlive/"). It could be done by a network installer (see [here]("http://tug.org/texlive/quickinstall.html")). texlive2007 could be uninstalled. To fulfill dependencies, for instance Kile depends on texlive-latex-base, the tool equivs could be used to install a dummy package for it, see [Kile and TeX Live 2008 on Ubuntu Linux]("http://texblog.net/latex-archive/linux/kile-texlive-2008-equivs/").

Stefan


--
[TeXblog.net]("http://texblog.net")

---

