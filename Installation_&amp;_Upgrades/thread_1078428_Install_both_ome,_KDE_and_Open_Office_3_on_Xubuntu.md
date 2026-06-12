---
title: "Install both ome, KDE and Open Office 3 on Xubuntu 8.10"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by rapachooie on 2009-02-23
Hi Guys,

I have searched the forums and could not find an answer to this question so I though I should just post.

Quite simply, I have Xubuntu and like it. But I like to change window managers (I'm quite new to linux and like to learn different aspects of each) so I want to install both gnome and KDE4 on this Xubuntu 8.10 that I have working relatively flawlessly (except 3d acceleration on my intel 965).

In any case, from the add/remove software section, I simply cannot find any Gnome install, and the KDE install tells me in the description that it cannot be installed on my system (a Toshiba L300 notebook: Intel Core Duo, Intel x3100 (965), 2GB Ram.

Now I do already have Kubuntu 8.10 live on disc but cant figure out how to install KDE into this Xubuntu build.  I have no discs with Gnome on them.

Furthermore, when I installed Open Office writer from the Xubuntu add/remove section, it installed 2.4 instead of 3 which is not what I want.

I should mention that I have default repositories installed (I am not even sure how to change them, which is something I actually would like to learn how to do as I cannot find "TrueCrypt" or the game "Python Kye" on the standard repos.

Also, I have applied all of the Xubuntu 8.10 updates to current.

Anyway I think thats everything, hope its not too much to ask.

Please let me know if I left anything out, which I undoubtedly did! 

Cheers,

Chewy

---

### Post by taurus on 2009-02-23
From a terminal, run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop  <-- for Gnome
sudo apt-get install kubuntu-desktop  <-- for KDE
```

---

### Post by rapachooie on 2009-02-23
Excellent, thanks! Worked perfectly.

That couldnt be easier.

In regards to installing OpenOffice 3, I found a link that explains how but it requires the addition of another repository and authentication key which is downloaded from them... that seems a little self-defeating to me... assumming there is malicious code in there somewhere.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

is the website... is that a good guide to follow or would I be better off avoiding such things?

Again, thanks in advance.

---

### Post by taurus on 2009-02-23
Just add a launchpad repo to your /etc/apt/sources.list for the latest version of OpenOffice.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by rapachooie on 2009-02-26
Thanks heaps for that! Worked a charm :)

---

