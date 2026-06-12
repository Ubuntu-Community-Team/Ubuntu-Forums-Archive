---
title: "Guide: Updating Repos for Older Versions of Ubuntu"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by ledzepjes on 2009-06-17
Guide: Updating Repos for Older Versions of Ubuntu
 this guide was good as of 2009-06-17

Today I had trouble trying to update my laptop. It is one of a couple in my house, and use them to try out different versions of Ubuntu. Today I tried to update Ubuntu Gutsy, but kept getting an errors: (probably since it's unsupported :-) )

[php]Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
[/php]I was not able to download or check for any new updates using update manager or synaptic package manager. I searched around the interwebs and came across a link to add two lines of code to the bottom of the source.list and I was back and running. Just type:

[php]owner@ubuntu-pc:~$ sudo gedit /etc/apt/sources.list[/php]
and add these two lines to the bottom:
[php]deb http://old-releases.ubuntu.com/ubuntu gutsy-updates main universe restricted multiverse
deb http://old-releases.ubuntu.com/ubuntu gutsy-security main universe restricted multiverse[/php]Also, you can edit the source.list file by adding # symbol infront of each deb which tells the update manager to ignore them so as not to get any more errors, but that's entirely not necessary, to each his own.

Here's the editing timeline:
1. Before editing my source.list and getting errors it looked like this:

[php]deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy main universe restricted multiverse
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted[/php]2. Then after editing by adding two deb's for the old repos and by adding # to delink the non-functioning repos (found the non-functioning links by adding and deleting # thru trial and error) the bottom of my source.list file now looks like this:
[php]deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

#deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy main universe restricted multiverse
deb http://ppa.launchpad.net/do-core/ubuntu gutsy main
deb-src http://ppa.launchpad.net/do-core/ubuntu gutsy main
#deb http://ubuntu.mirrors.tds.net/pub/ubuntu/ gutsy-updates universe main multiverse restricted
#deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://old-releases.ubuntu.com/ubuntu gutsy-updates main universe restricted multiverse
deb http://old-releases.ubuntu.com/ubuntu gutsy-security main universe restricted multiverse[/php]Happy trails :p. Now I can update 7.10 gutsy with no errors.


References:

[http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)
[https://lists.ubuntu.com/archives/ubuntu-users/2009-May/186227.html](https://lists.ubuntu.com/archives/ubuntu-users/2009-May/186227.html)
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)
and me, ledzepjes

---

