---
title: "Installing xvidcap_1.1.7_i386.deb"
date: 2008-09-16
forum: General Help
---

### Post by qscfthm on 2008-09-16
Hi,
   I want xvidcap in my ubuntu gutsy.But When Open xvidcap_1.1.7_i386.deb it displays
[COLOR="Red"]dependency not satisfactory:libc6[/COLOR]
I really wanted xvidcao to capture the screen videos.
Plz help me wirh this.:-|

---

### Post by ryanhaigh on 2008-09-16
Without the full error message it is impossible to be certain but I would guess that the deb you have requries a later version of libc6 than what is available in gutsy, most likely the deb is for hardy or another distro.

[A search of packages.ubuntu.com]("http://packages.ubuntu.com/search?keywords=xvidcap") indicates that there is no official xvidcap package for gutsy which is strange because it is mentioned on the launchpad page.

I would suggest trying some of the older versions of the package available via sourceforge:
[http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441](http://sourceforge.net/project/showfiles.php?group_id=81535&package_id=83441)

Other than that you could try a different package such as [apt://gtk-recordmydesktop]("apt://gtk-recordmydesktop")

---

