---
title: "Old versions removed from repositories"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by raj001 on 2009-05-08
Hello all there. I hope somebody from Canonical is reading this sometimes, because I want to express my great disappointment because of the fact that branches for old versions (especially 7.10 gutsy, which I'm still using) have been recently removed from Ubuntu repositories and all their mirrors.
As far as I remember, this is first time something like this has been done. Until now old versions, for which support has ended, were still present in the repositoreis, so you could - if you wanted to - install them again, or add new packages to the system you already have. With the "gutsy" branch removed from repositories, it is not possible anymore neither to install the system (you can't get any updates, you can't install language packs - which are automatically downloaded from repositories during installation!, you ca't install missing codecs for mp3, xvid etc.) nor to add any software to the system you already have using apt, synaptic or Add/Remove from the main menu...
I think this is a very bad way to force people to upgrade. Even Microsoft does not remove from their Windows Update website the updates for old versions of Windows - eg. Windows 98, that is not supported by them anymore for quite a time. Here we have no updates, nothing at all! Removing the old branches from repositiories makes older systems that are still running much less useful.
This is not the "ubuntu" spirit - this is not nice to the users! Please restore the old repository branches.

---

### Post by Partyboi2 on 2009-05-08
Hi, You still do have the option to to install packages in Gutsy if you do not want to upgrade (recommended) the repos are no longer listed under the Ubuntu ones but you can comment out your current sources and add 
```
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main/debian-installer
deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
```old-releases.ubuntu.com are where all the old release repos are.

---

### Post by HyRax on 2009-05-08
> **raj001 said:**
> 
This is not the "ubuntu" spirit - this is not nice to the users! Please restore the old repository branches.

Considering that the software is free and that when software is no longer supported that Canonical don't actually have any obligation to store the old repositories (even though they do), I think it's a bit rich to make pseudo demands of them and compare them to the likes of Microsoft who do charge insane amiunts of money for their software to the point that you WOULD expect them to retain old updates to their software!

No, you're not obligated to upgrade, but at the same time you're doing yourself a disservice because you're missing out on future advances and you're also leaving yourself open to any major security exploits that are corrected in later versions of the OS.

Remember that Ubuntu and Linux in general is not Windows. It does not require that you upgrade your PC's hardware with each new release. Even Ubuntu Jaunty 9.04 has very modest disk and memory requirements compared to Windows and Ubuntu's system requirements by and large have not changed between each release of Ubuntu from Day One. My EeePC 701 with its modest gfx and processing power is now flying under Jaunty. It boots faster, runs faster (except for 3D gfx for the moment) and the battery life has been markedly improved. I would never go back to the older versions of Ubuntu which are now directly slower and clunkier than the Jaunty release.

---

### Post by raj001 on 2009-05-08
> **HyRax said:**
> Considering that the software is free and that when software is no longer supported that Canonical don't actually have any obligation to store the old repositories (even though they do), I think it's a bit rich to make pseudo demands of them and compare them to the likes of Microsoft who do charge insane amiunts of money for their software to the point that you WOULD expect them to retain old updates to their software!

I'm not comparing Canonical to Microsoft, I only wanted to make a point that even Microsoft, who is purely business-oriented, does retain the old updates. And I'm thinking one would NOT expect that from Microsft actually, because people who still use old Windows (which they don't sell anymore) wouldn't bring them any money. People who upgrade to new versions of Windows, on the other hand, would do. So form a pure business point of view, there is no reason for them to keep old updates.
But from the people who are active in the FLOSS development one would generally expect an attitude of more "towards users", so one would not expect removing old versions.

Anyway, I'm glad that someone pointed me to the old-releases repo, as it seemingly is not accessible directly from the main Ubuntu page by some link... Thanks!

> 
No, you're not obligated to upgrade, but at the same time you're doing yourself a disservice because you're missing out on future advances and you're also leaving yourself open to any major security exploits that are corrected in later versions of the OS.

Remember that Ubuntu and Linux in general is not Windows. It does not require that you upgrade your PC's hardware with each new release.I know very well that Linux is not Windows and does not have so enormous system requirements. I've been working with different Linux distributions for years, starting from SLS that was even before Slackware.
However, there is always - with ANY software - the possibility that with a major upgrade, something that was working previously unexpectedly breaks. I hate such situations and want to avoid them as much as I can, therefore I am not eager to upgrade, and with almost all software I use, I'm usually a few versions behind the current one. I'm fully aware that I'm missing new features etc. but I follow the principle that "if something works, don't fix it". If I would actually **need** one of the new features, then I would consider an upgrade.

---

