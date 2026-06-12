---
title: "upgrading pidgin 2.5.2 to 2.5.4"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by heartwarmer on 2009-01-27
HI
I have pidgin 2.5.2 on ubuntu 8.10 ok, so i downloaded 2.5.4 source from the site, and built a deb installer.
my question is do I just install the new package? or should I first remove the old one?
the important thing for me is keeping the settings and plugins.. is it possible?

---

### Post by kostkon on 2009-01-27
You can just download it from [here]("http://www.getdeb.net/app/Pidgin"). Double-click on it to install it (you don't need to remove the old one first). It will keep your plugins and settings.

---

### Post by heartwarmer on 2009-01-27
thanx for the fast reply =), the deb that i built wont install cuz it says that a later version is already installed!!
in the link you gave me in intrepid 32bit there are 4 packages, do i have to install them all?

---

### Post by kostkon on 2009-01-27
> **heartwarmer said:**
> thanx for the fast reply =), the deb that i built wont install cuz it says that a later version is already installed!!
in the link you gave me in intrepid 32bit there are 4 packages, do i have to install them all?
Yes, all.

Install them in this order: *pidgin-data*, then *libpurple0*, *libpurple-bin*, and finally the *pidgin* package.

---

### Post by kevdog on 2009-01-27
If you compile from source you can have both 2.5.2 and 2.5.4 installed on your system without conflict between the two versions.

---

### Post by navjotjsingh on 2009-01-28
> **kostkon said:**
> Yes, all.

Install them in this order: *pidgin-data*, then *libpurple0*, *libpurple-bin*, and finally the *pidgin* package.

I tried your method without removing older versions, but when I tried installing pidgin-data, it failed saying:

> Error: Failed to satisfy all dependencies (broken cache)

---

### Post by heartwarmer on 2009-01-28
yes the same happened with me, i had to run "sudo apt-get install -f" and then it worked.
but i should note, look at the packages that will be removed, because you may need to reinstall some of them like guifications, dont worry it didnt delete my settings.

---

### Post by heartwarmer on 2009-01-29
how can i do that? installing from source not affecting the already installed one?

---

### Post by kevdog on 2009-01-29
Installing from source by defaults puts the executables in /usr/local/bin.  The package installations (.deb) put the executables in /usr/bin.

Here:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

---

### Post by heartwarmer on 2009-01-29
i installed it from source after applying a couple of patches, it worked but it replaced files in usr/share/pixmap/pidgin (i was using a custom icon pack), i didnt notice any other change, is it expected to do this?

---

### Post by kevdog on 2009-01-30
Depends how you compiled it?

Because it should be installed in the /usr/local tree, you should have seen things placed inside: /usr/local/share/pixmaps/pidgin

Again the installed version is going to be inside the /usr tree and the compiled version inside the /usr/local tree.  Unless you have created symbolic or hard links between the two directory trees, the information should be kept separate.

Just out of interest, what patches did you apply and what was the syntax of your ./configure statement?  If you used ./configure --path=/usr  then all bets are off since this will place the compiled version inside the /usr tree (rather than the default /usr/local tree).

---

### Post by heartwarmer on 2009-01-30
OMG!! am an idiot
i ran 
./configure: '--build=i486-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/pidgin' '--disable-maintainer-mode' '--disable-dependency-tracking' '--disable-gevolution' '--enable-cap' '--with-system-ssl-certs=/etc/ssl/certs' '--enable-perl' '--with-zephyr=/usr' '--enable-dbus' '--enable-gnutls=no' '--enable-nss=yes' '--enable-cyrus-sasl' 'build_alias=i486-linux-gnu' 'CC=cc' 'CFLAGS=-fstack-protector' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS='

no wonder it did that, so doing only a './configure' would install it right??
and the patches were one for buddy icon not showing, and the other for colored nicknames.and btw they both didnt work.

---

### Post by s3kt0r on 2009-01-30
Yeah, we're supposed to check out info from more sources than just one person..."You don't need to uninstall previous version"..
Thanks for the debs though.

:mad:

sudo apt-get install -f

---

