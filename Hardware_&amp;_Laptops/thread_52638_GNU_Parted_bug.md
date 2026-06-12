---
title: "GNU Parted bug?"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by Kvetch on 2005-07-28
Hello, I recently got a new system and have had issues getting XP and Linux to work in a dual boot setup.  My new system is an AMD 3000+ socket 939, 1gb ram, 164gb Hitachi SATA II, Geforce 6600.  Basically if I install XP on /dev/sda1 then install Linux on /dev/sda2, Grub allows me to boot into Linux (Ubuntu) but XP stops loading on mup.sys and just hangs.  I have tried getting my system to work with Ubuntu and Gentoo.  After install both fail to load XP.  I believe that this is my issue.
[http://ubuntuforums.org/archive/index.php/t-1396.html](http://ubuntuforums.org/archive/index.php/t-1396.html)
[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/)
[http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html)
[http://www.redhat.com/archives/fedora-test-list/2004-May/msg02114.html](http://www.redhat.com/archives/fedora-test-list/2004-May/msg02114.html)
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980)
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=113201](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=113201)

I believe the version of Ubuntu (5.04) I am using has the GNU parted bug in it also.  Does anyone know if this is true.  If so how to bypass it or create a 5.04 ISO with a newer parted version?

Thanks,
Nick

---

### Post by az on 2005-07-28
[QUOTE=Kvetch]Hello, I recently got a new system and have had issues getting XP and Linux to work in a dual boot setup.  My new system is an AMD 3000+ socket 939, 1gb ram, 164gb Hitachi SATA II, Geforce 6600.  Basically if I install XP on /dev/sda1 then install Linux on /dev/sda2, Grub allows me to boot into Linux (Ubuntu) but XP stops loading on mup.sys and just hangs.  I have tried getting my system to work with Ubuntu and Gentoo.  After install both fail to load XP.  I believe that this is my issue.
[http://ubuntuforums.org/archive/index.php/t-1396.html](http://ubuntuforums.org/archive/index.php/t-1396.html)
[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/)
[http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html](http://portal.suse.com/sdb/en/2004/05/fhassel_windows_not_booting91.html)
[http://www.redhat.com/archives/fedora-test-list/2004-May/msg02114.html](http://www.redhat.com/archives/fedora-test-list/2004-May/msg02114.html)
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=115980)
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=113201](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=113201)

I believe the version of Ubuntu (5.04) I am using has the GNU parted bug in it also.  Does anyone know if this is true.  If so how to bypass it or create a 5.04 ISO with a newer parted version?

Thanks,
Nick[/QUOTE]

Did you create any partition with Partition Magic, as described in the bug reports you cite?

---

### Post by Kvetch on 2005-07-28
No I did not.  What post says something about Part Magic?

---

