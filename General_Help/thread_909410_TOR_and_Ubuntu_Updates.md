---
title: "TOR and Ubuntu Updates"
date: 2008-09-03
forum: General Help
---

### Post by dokktorwho222 on 2008-09-03
Hi, just looking for a little help here. I've installed TOR and FoxyProxy on my laptop - they work fine. The problem i have is when i try to run my updates for Ubuntu - the update manager works fine and the updates come up but when i try to install them i get something like this:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1ubuntu3_i386.deb)
  Could not resolve 'localhost: 8118'

How can i get my updates without removing the TOR program?
thanks

---

### Post by dokktorwho222 on 2008-09-04
Bump. I'd like to see if someone has an answer to this problem.

---

### Post by dark_phantom on 2008-09-04
Tor is in the repositories, you don't need to implicitly list it in the sources list.  Probably you have an extra line in the sources.list file that is not resolving and that's what the message is coming from.  Post up your /etc/apt/sources.list file.

---

### Post by dokktorwho222 on 2008-09-06
is this what you're looking for?


C# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/
gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

---

