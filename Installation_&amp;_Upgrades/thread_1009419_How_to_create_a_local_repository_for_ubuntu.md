---
title: "How to create a local repository for ubuntu ???"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by isaacrc82 on 2008-12-12
Hi everybody:

I want to create a local repository of ubuntu.
I have installed the 8.0.4 ubuntu version in my computer and I want to upgrade it to intrepid Ibex.

I have gotten the whole repository of 8.10 ubuntu version, the file structure of the folder is the following:

--ubuntu-intrepid
------.temp
--------- dists
------------ intrepid
------------------ main
------------------ multiverse
------------------ restricted
------------------ universe
------pool
--------- main
--------- multiverse
--------- restricted
--------- universe
------project

But when I follow the steps to do a local repository:
sudo dpkg-scansources /ubuntu-intrepid /dev/null | gzip -9c> /ubuntu-intrepid/Sources.gz
sudo dpkg-scanpackages /ubuntu-intrepid /dev/null | gzip -9c> /ubuntu-intrepid/Packages.gz

The files Sources.gz and Packages.gz are not build.
Besides when I add the "file:/repo/ubuntu-intrepid" entry to the /etc/sources.lst it doesn't work.
Could somebody help me to do this in the right way ???
I hope you can help me.
Regards
Ariel

---

### Post by pietjanjaap on 2008-12-12
Debmirror you need, search the forum.

I used my hatddisk places, these you should replace.
Debmirror you find on the site, because it is not anymore in ubuntu.
You can leave everythimg on yor pc as repository, or make dvd's from it.
leave it on your pc, then start the first part(1,2,3) then it will only update, to keep up to date.

first
1 Hardy Heron's repository
debmirror --nosource -m --passive --host=archive.ubuntu.com --root=ubuntu/ --method=ftp --progress --dist=hardy,hardy-security,hardy-updates,hardy-backports, --section=main,restricted,universe,multiverse --arch=i386 ~/UbuntuRepos --ignore-release-gpg
2 Canonical Repos
debmirror --nosource -m --passive --host=archive.canonical.com --root=/ --method=http --progress --dist=hardy,hardy-backports,hardy-proposed,hardy-security,hardy-updates --section=partner --arch=i386 ~/CanonicalRepos --ignore-release-gpg
3 MediBuntu Repos
debmirror --nosource -m --passive --host=packages.medibuntu.org --root=/ --method=http --progress --dist=hardy --section=free,non-free --arch=i386 ~/MediBuntuRepos --ignore-release-gpg

second

4 Divide into DVD-sized portions
debpartial --nosource --dirprefix=ubuntu --section=main,restricted,universe,multiverse --dist=hardy,hardy-security,hardy-updates,hardy-backports --size=DVD ~/UbuntuRepos ~/UbuntuDVDs


Part 2:
How many CDs will we need to create? How do we find out? Paste this code in the Terminal and hit Enter:
Code:

ls -l ~/UbuntuDVDs

If the last folder is ubuntu3 you need to create 4 DVDs. If the last folder is ubuntu4 then it will be 5 DVDs, and if the last folder is ubuntu31, you'll need to create 32 CDs, and so on.
Code:

ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu0

Code:

ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu1

Code:

ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu2

Code:

ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu3

Code:

ruby debcopy -l ~/UbuntuRepos ~/UbuntuDVDs/ubuntu4

---

### Post by isaacrc82 on 2008-12-15
I don't have internet conection, I have already copied to the hard disk the entire intrepid ibex repository.
What I want to do is to upgrade from the repository I have in my hard disk, I am not able to do this because I am newbie using ubuntu linux.
Regards.

---

### Post by isaacrc82 on 2008-12-15
I have already made the upgrade to intrepid ubuntu from hardy. The problem was in the /etc/apt/sources.lst.
The problem now is that in the /etc/apt/sources.lst I have the hardy urls to upgrade my past hardy ubuntu, I need now to put in the source.lst file the url to point to the intrepid repositories, Could somebody give me these urls ???
I hope you can help me.
Greetings
Ariel

---

### Post by shaggy999 on 2009-01-14
I think the problem with your sources.list is that you need **THREE** /'s right after file:

Here's an example of how my local repository is used in my sources.list:

deb file:///media/software/apt-mirror/mirror/ubuntu.osuosl.org/ubuntu intrepid main restricted universe multiverse
deb file:///media/software/apt-mirror/mirror/ubuntu.osuosl.org/ubuntu intrepid-updates main restricted universe multiverse
deb file:///media/software/apt-mirror/mirror/ubuntu.osuosl.org/ubuntu intrepid-security main restricted universe multiverse
deb file:///media/software/apt-mirror/mirror/packages.medibuntu.org intrepid free non-free

The reason for needing three forward slashes is because you first need two to go after file just as with http:// and THEN you need to put a path after that starting with / (the root) directory. Fix that in your sources.list file and you should be good to go!

---

