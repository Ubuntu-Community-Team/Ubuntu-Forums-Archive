---
title: "Local mirror : How to make a partial update ?"
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by benj.david on 2009-10-05
Hi everyone,
I have a local Ubuntu mirror which does not synchronize automatically with the official ones. (which is deliberate)

As Jaunty official mirror has been updated, I would like to update mine but only packages (and their dependencies) I've chosen.

I've seen this kind of command:
debmirror --progress -m --passive -h ftp.de.debian.org -e ftp -d sarge --getcontents --exclude=".*-dev.*" /home/moi/mirror/
to exclude packages from the update, but I would do the opposite : include *only* what I want...

If anyone has the magical command or tool...

Thank you,
ben

---

### Post by ermeyers on 2009-10-06
I looked into this a little bit, and I found a package apt-show-versions that will let you see what is "--upgradeable", then you can install or download an upgrade that you select.  It's a Perl script, so you can easily modify it.  I also found packages deborphan and debfoster which may be of some use.

---

### Post by benj.david on 2009-10-06
Hello ermeyers,
Thank you for the reply, I did know about this script (too many apt-* :) )

Anyway, this script is great for an end-user but I need something to partially update my mirror from an official Ubuntu one, not my own computer.
After some googling, this is maybe possible with reprepro and the Filter* arguments
[http://mirrorer.alioth.debian.org/reprepro.1.html](http://mirrorer.alioth.debian.org/reprepro.1.html)

---

### Post by benj.david on 2009-10-09
Hi all,
I finally found the solution with reprepro, but not using the Filter arguments..

- Build the repository with reprepro (reprepro update)

When the official repository has been updated :
- Check the mirror differences by comparing local and remote "Packages" file
- Manage the dependencies using seed and germinate (see the tutorial bellow)
- Download the deb files (aptitude download)
- Update your local repository (reprepro includedeb)



Many thanks to this tutorial : [http://lostwebsite.wordpress.com/2008/10/21/partial-debian-mirrors/](http://lostwebsite.wordpress.com/2008/10/21/partial-debian-mirrors/)

---

### Post by ermeyers on 2009-10-09
Thanks for coming back with the solution you found.  I'll check it out.

---

